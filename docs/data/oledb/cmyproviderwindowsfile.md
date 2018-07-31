---
title: CMyProviderWindowsFile |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyproviderwindowsfile
dev_langs:
- C++
helpviewer_keywords:
- CMyProviderWindowsFile class
- OLE DB providers, wizard-generated files
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0f18f5a524cbfbfa7f17dfd3964c68329bc8a042
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338502"
---
# <a name="cmyproviderwindowsfile"></a>CMyProviderWindowsFile
精靈會建立類別可以包含一個資料列的資料;在此情況下，它會呼叫`CMyProviderWindowsFile`。 下列程式碼會針對`CMyProviderWindowsFile`產生的精靈，並使用列出目錄中的所有檔案`WIN32_FIND_DATA`結構。 `CMyProviderWindowsFile` 繼承自`WIN32_FIND_DATA`結構：  
  
```cpp
/////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
  
class CMyProviderWindowsFile:   
   public WIN32_FIND_DATA  
{  
public:  
BEGIN_PROVIDER_COLUMN_MAP(CMyProviderWindowsFile)  
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)  
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)  
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)  
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)  
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)  
END_PROVIDER_COLUMN_MAP()  
};  
```  
  
 `CMyProviderWindowsFile` 會呼叫[使用者記錄類別](../../data/oledb/user-record.md)因為它也包含描述提供者的資料列集中的資料行對應。 提供者資料行對應會包含每個欄位中使用 PROVIDER_COLUMN_ENTRY 巨集的資料列集的一個項目。 巨集指定資料行名稱、 序數和位移結構項目。 在上述程式碼中的提供者的資料行項目包含的位移`WIN32_FIND_DATA`結構。 當取用者呼叫`IRowset::GetData`，資料會傳輸一個連續的緩衝區中。 與其讓您執行指標算術，地圖可讓您指定的資料成員。  
  
 `CMyProviderRowset`類別也包含`Execute`方法。 `Execute` 是什麼實際讀取中的資料來源的原生。 下列程式碼會顯示精靈產生`Execute`方法。 此函數會使用 Win32`FindFirstFile`並`FindNextFile`Api 來擷取目錄中檔案的相關資訊，並將它們放在執行個體中的`CMyProviderWindowsFile`類別。  
  
```cpp
/////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
  
HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)  
{  
   USES_CONVERSION;  
   BOOL bFound = FALSE;  
   HANDLE hFile;  
   LPTSTR  szDir = (m_strCommandText == _T("")) ? _T("*.*") :  
       OLE2T(m_strCommandText);  
   CMyProviderWindowsFile wf;  
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
  
 要搜尋的目錄由`m_strCommandText`; 這包含所代表的文字`ICommandText`命令物件中的介面。 如果未不指定任何目錄，它會使用目前的目錄。  
  
 方法會建立一個項目，每個檔案 （對應至一個資料列），並將它放入`m_rgRowData`資料成員。 `CRowsetImpl`類別會定義`m_rgRowData`資料成員。 此陣列中的資料代表整個資料表，而整個範本中使用。  
  
## <a name="see-also"></a>另請參閱  
 [提供者精靈產生的檔案](../../data/oledb/provider-wizard-generated-files.md)