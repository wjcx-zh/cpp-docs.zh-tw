---
title: 將字串讀入 OLE DB 提供者內
ms.date: 10/13/2018
helpviewer_keywords:
- OLE DB providers, reading strings into
ms.assetid: 517f322c-f37e-4eed-bf5e-dd9a412c2f98
ms.openlocfilehash: d46b4e1a53e7e489763f40e7a5238e65b493f7c8
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027424"
---
# <a name="reading-strings-into-the-ole-db-provider"></a>將字串讀入 OLE DB 提供者內

`CCustomRowset::Execute`函式開啟的檔案和讀取字串。 取用者傳遞給提供者的檔案名稱，藉由呼叫[icommandtext:: Setcommandtext](/previous-versions/windows/desktop/ms709757(v=vs.85))。 提供者接收的檔案名稱，並將它儲存在成員變數`m_strCommandText`。 `Execute` 讀取的檔案名稱`m_strCommandText`。 如果檔案名稱無效，或檔案無法使用，`Execute`會傳回錯誤。 否則，它會開啟檔案，並在呼叫`fgets`來擷取字串。 針對每個設定的字串讀取`Execute`建立使用者記錄的執行個體 (修改`CCustomWindowsFile`從[OLE DB 提供者中的儲存字串](../../data/oledb/storing-strings-in-the-ole-db-provider.md)) 並將它放入陣列。

如果無法開啟檔案，`Execute`必須傳回 DB_E_NOTABLE。 如果它改為傳回 E_FAIL，提供者不會使用許多消費者來說並不會傳遞 OLE DB[一致性測試](../../data/oledb/testing-your-provider.md)。

## <a name="example"></a>範例

```cpp
/////////////////////////////////////////////////////////////////////////
// CustomRS.h
class CCustomRowset : public CRowsetImpl< CCustomRowset, CCustomWindowsFile, CCustomCommand>
{
public:
    HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)
    {
        enum {
            sizeOfBuffer = 256,
            sizeOfFile = MAX_PATH
        };
        USES_CONVERSION;
        FILE* pFile = NULL;
        TCHAR szString[sizeOfBuffer];
        TCHAR szFile[sizeOfFile];
        size_t nLength;

        ObjectLock lock(this);

        // From a filename, passed in as a command text, scan the file
        // placing data in the data array.
        if (!m_strCommandText)
        {
            ATLTRACE("No filename specified");
            return E_FAIL;
        }

        // Open the file
        _tcscpy_s(szFile, sizeOfFile, m_strCommandText);
        if (szFile[0] == _T('\0') ||
            (fopen_s(&pFile, (char*)&szFile[0], "r") == 0))
        {
            ATLTRACE("Could not open file");
            return DB_E_NOTABLE;
        }

        // Scan and parse the file.
        // The file should contain two strings per record
        LONG cFiles = 0;
        while (fgets((char*)szString, sizeOfBuffer, pFile) != NULL)
        {
            nLength = strnlen((char*)szString, sizeOfBuffer);
            szString[nLength-1] = '\0';   // Strip off trailing CR/LF
            CCustomWindowsFile am;
            _tcscpy_s(am.szCommand, am.iSize, szString);
            _tcscpy_s(am.szCommand2, am.iSize, szString);

            if (fgets((char*)szString, sizeOfBuffer, pFile) != NULL)
            {
                nLength = strnlen((char*)szString, sizeOfBuffer);
                szString[nLength-1] = '\0'; // Strip off trailing CR/LF
                _tcscpy_s(am.szText, am.iSize, szString);
                _tcscpy_s(am.szText2, am.iSize, szString);
            }

            am.dwBookmark = ++cFiles;
            if (!m_rgRowData.Add(am))
            {
                ATLTRACE("Couldn't add data to array");
                fclose(pFile);
                return E_FAIL;
            }
        }

        if (pcRowsAffected != NULL)
            *pcRowsAffected = cFiles;
        return S_OK;
    }
};
```

當這麼做時，您的提供者應該可以編譯及執行。 若要測試的提供者，您需要有比對功能的取用者。 [實作簡單消費者](../../data/oledb/implementing-a-simple-consumer.md)示範如何建立這類測試取用者。 提供者執行測試的取用者，並確認測試取用者會從提供者擷取適當的字串。

當您已成功通過測試您的提供者時，您可以藉由實作額外的介面增強其功能。 範例所示[增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)。

## <a name="see-also"></a>另請參閱

[實作簡單唯讀提供者](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
