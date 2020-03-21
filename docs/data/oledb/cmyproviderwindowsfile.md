---
title: CCustomWindowsFile
ms.date: 10/22/2018
f1_keywords:
- cmyproviderwindowsfile
- ccustomwindowsfile
helpviewer_keywords:
- CMyProviderWindowsFile class
- OLE DB providers, wizard-generated files
- CCustomWindowsFile class
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
ms.openlocfilehash: 103a1ce5568c6137994056e574ce8eec04511d8f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079749"
---
# <a name="ccustomwindowsfile"></a>CCustomWindowsFile

Wizard 會建立一個具有一個資料列的類別;在此情況下，它會被稱為 `CCustomWindowsFile`。 下列 `CCustomWindowsFile` 的程式碼會產生 wizard，並使用 `WIN32_FIND_DATA` 結構列出目錄中的所有檔案。 `CCustomWindowsFile` 繼承自 `WIN32_FIND_DATA` 結構：

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H

class CCustomWindowsFile:
   public WIN32_FIND_DATA
{
public:
BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)
END_PROVIDER_COLUMN_MAP()
};
```

`CCustomWindowsFile` 稱為[使用者記錄類別](../../data/oledb/user-record.md)，因為它也有一個對應，描述提供者資料列集中的資料行。 提供者資料行對應會針對資料列集中的每個欄位，使用 PROVIDER_COLUMN_ENTRY 宏來包含一個專案。 宏會針對結構專案指定資料行名稱、序數和位移。 上述程式碼中的提供者資料行專案包含 `WIN32_FIND_DATA` 結構中的位移。 當取用者呼叫 `IRowset::GetData`時，資料會在一個連續的緩衝區中傳輸。 對應可讓您指定資料成員，而不是讓您執行指標算術。

`CCustomRowset` 類別也包含 `Execute` 方法。 `Execute` 實際上是從原生來源讀取中的資料。 下列程式碼顯示 wizard 產生的 `Execute` 方法。 函式會使用 Win32 `FindFirstFile` 和 `FindNextFile` Api 來抓取目錄中的檔案相關資訊，並將它們放在 `CCustomWindowsFile` 類別的實例中。

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H

HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)
{
   USES_CONVERSION;
   BOOL bFound = FALSE;
   HANDLE hFile;
   LPTSTR  szDir = (m_strCommandText == _T("")) ? _T("*.*") :
       OLE2T(m_strCommandText);
   CCustomWindowsFile wf;
   hFile = FindFirstFile(szDir, &wf);
   if (hFile == INVALID_HANDLE_VALUE)
      return DB_E_ERRORSINCOMMAND;
   LONG cFiles = 1;
   BOOL bMoreFiles = TRUE;
   while (bMoreFiles)
   {
      if (!m_rgRowData.Add(wf))
         return E_OUTOFMEMORY;
      bMoreFiles = FindNextFile(hFile, &wf);
      cFiles++;
   }
   FindClose(hFile);
   if (pcRowsAffected != NULL)
      *pcRowsAffected = cFiles;
   return S_OK;
}
```

要搜尋的目錄會顯示 `m_strCommandText`;這包含命令物件中 `ICommandText` 介面所表示的文字。 如果未指定目錄，則會使用目前的目錄。

方法會為每個檔案建立一個專案（對應到一個資料列），並將它放在 `m_rgRowData` 的資料成員中。 `CRowsetImpl` 類別會定義 `m_rgRowData` 資料成員。 此陣列中的資料會顯示在整個資料表中，並在整個範本中使用。

## <a name="see-also"></a>另請參閱

[提供者精靈產生的檔案](../../data/oledb/provider-wizard-generated-files.md)<br/>
