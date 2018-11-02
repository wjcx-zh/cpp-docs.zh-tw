---
title: 將字串讀入 OLE DB 提供者內
ms.date: 10/13/2018
helpviewer_keywords:
- OLE DB providers, reading strings into
ms.assetid: 517f322c-f37e-4eed-bf5e-dd9a412c2f98
ms.openlocfilehash: 4883edf08097f8dcdb18b821e9a0ca37f1ff6b0f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469663"
---
# <a name="reading-strings-into-the-ole-db-provider"></a>將字串讀入 OLE DB 提供者內

`RCustomRowset::Execute`函式開啟的檔案和讀取字串。 取用者傳遞給提供者的檔案名稱，藉由呼叫[icommandtext:: Setcommandtext](/previous-versions/windows/desktop/ms709757)。 提供者接收的檔案名稱，並將它儲存在成員變數`m_szCommandText`。 `Execute` 讀取的檔案名稱`m_szCommandText`。 如果檔案名稱無效，或檔案無法使用，`Execute`會傳回錯誤。 否則，它會開啟檔案，並在呼叫`fgets`來擷取字串。 針對每個設定的字串讀取`Execute`建立使用者記錄的執行個體 (`CAgentMan`) 並將它放入陣列。

如果無法開啟檔案，`Execute`必須傳回 DB_E_NOTABLE。 如果它改為傳回 E_FAIL，提供者不會使用許多消費者來說並不會傳遞 OLE DB[一致性測試](../../data/oledb/testing-your-provider.md)。

## <a name="example"></a>範例

```cpp
/////////////////////////////////////////////////////////////////////////
// CustomRS.h
class RCustomRowset : public CRowsetImpl< RCustomRowset, CAgentMan, CRCustomCommand>
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
        size_t nLength;        errcodeerr;

        ObjectLock lock(this);

        // From a filename, passed in as a command text, scan the file
        // placing data in the data array.
        if (!m_szCommandText)
        {
            ATLTRACE("No filename specified");
            return E_FAIL;
        }

        // Open the file
        _tcscpy_s(szFile, sizeOfFile, m_szCommandText);
        if (szFile[0] == _T('\0') ||
            ((err = fopen_s(&pFile, &szFile[0], "r")) == 0))
        {
            ATLTRACE("Could not open file");
            return DB_E_NOTABLE;
        }

        // Scan and parse the file.
        // The file should contain two strings per record
        LONG cFiles = 0;
        while (fgets(szString, sizeOfBuffer, pFile) != NULL)
        {
            nLength = strnlen(szString, sizeOfBuffer);
            szString[nLength-1] = '\0';   // Strip off trailing CR/LF
            CAgentMan am;
            _tcscpy_s(am.szCommand, am.sizeOfCommand, szString);
            _tcscpy_s(am.szCommand2, am.sizeOfCommand2, szString);

            if (fgets(szString, sizeOfBuffer, pFile) != NULL)
            {
                nLength = strnlen(szString, sizeOfBuffer);
                szString[nLength-1] = '\0'; // Strip off trailing CR/LF
                _tcscpy_s(am.szText, am.sizeOfText, szString);
                _tcscpy_s(am.szText2, am.sizeOfText2, szString);
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
}
```

## <a name="see-also"></a>另請參閱

[實作簡單唯讀提供者](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
