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
ms.openlocfilehash: 008fe318ee96248dfca0c3c87bf660726beb3092
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660820"
---
# <a name="ccustomwindowsfile"></a>CCustomWindowsFile

精靈會建立具有一個資料列的資料; 的類別在此情況下，它會呼叫`CCustomWindowsFile`。 下列程式碼會針對`CCustomWindowsFile`產生的精靈，並使用列出目錄中的所有檔案`WIN32_FIND_DATA`結構。 `CCustomWindowsFile` 繼承自`WIN32_FIND_DATA`結構：

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

`CCustomWindowsFile` 會呼叫[使用者記錄類別](../../data/oledb/user-record.md)因為它也描述提供者的資料列集中的資料行的對應。 提供者資料行對應會包含每個欄位中使用 PROVIDER_COLUMN_ENTRY 巨集的資料列集的一個項目。 巨集指定資料行名稱、 序數和位移結構項目。 在上述程式碼中的提供者的資料行項目包含的位移`WIN32_FIND_DATA`結構。 當取用者呼叫`IRowset::GetData`，資料會傳輸一個連續的緩衝區中。 與其讓您執行指標算術，地圖可讓您指定的資料成員。

`CCustomRowset`類別也包含`Execute`方法。 `Execute` 是什麼實際讀取中的資料來源的原生。 下列程式碼會顯示精靈產生`Execute`方法。 此函數會使用 Win32`FindFirstFile`並`FindNextFile`Api 來擷取目錄中檔案的相關資訊，並將它們放在執行個體中的`CCustomWindowsFile`類別。

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

要搜尋的目錄會顯示`m_strCommandText`; 這包含所代表的文字`ICommandText`命令物件中的介面。 如果未不指定任何目錄，它會使用目前的目錄。

方法會建立一個項目，每個檔案 （對應至一個資料列），並將它放入`m_rgRowData`資料成員。 `CRowsetImpl`類別會定義`m_rgRowData`資料成員。 此陣列中的資料會顯示整個資料表，並使用到所有的範本。

## <a name="see-also"></a>另請參閱

[提供者精靈產生的檔案](../../data/oledb/provider-wizard-generated-files.md)<br/>
