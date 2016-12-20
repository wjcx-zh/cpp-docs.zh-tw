---
title: "CMyProviderWindowsFile | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cmyproviderwindowsfile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMyProviderWindowsFile 類別"
  - "OLE DB 提供者, 精靈產生的檔案"
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMyProviderWindowsFile
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

精靈會建立一個包含資料列的類別 \(Class\)；在本範例中，該類別名為 `CMyProviderWindowsFile`。  下列是由精靈產生的 `CMyProviderWindowsFile` 程式碼，它使用 **WIN32\_FIND\_DATA** 結構列出了目錄中的所有檔案。  `CMyProviderWindowsFile` 繼承自 **WIN32\_FIND\_DATA** 結構：  
  
```  
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
  
 `CMyProviderWindowsFile` 稱為[使用者資料錄類別](../../data/oledb/user-record.md)，因為它也包含用來描述提供者資料列集內資料行的對應。  提供者資料行對應包含了使用 PROVIDER\_COLUMN\_ENTRY 巨集之資料列集的每個欄位項目。  巨集指定了資料行名稱、序數以及結構項目的位移 \(Offset\)。  上述程式碼內的提供者資料行項目包含了 **WIN32\_FIND\_DATA** 結構的位移。  當消費者呼叫 **IRowset::GetData** 時，資料將在一個連續的緩衝區內傳輸。  這個對應不只可讓您進行指標算術，還可讓您指定資料成員。  
  
 `CMyProviderRowset` 類別也包含 `Execute` 方法。  `Execute` 會實際地自原生 \(Native\) 來源讀取資料。  下列程式碼會顯示精靈產生的 `Execute` 方法。  此函式使用 Win32 **FindFirstFile** 和 `FindNextFile` API 來擷取目錄內檔案的相關資訊，並將它們放在 `CMyProviderWindowsFile` 類別的執行個體 \(Instance\) 內。  
  
```  
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
  
 `m_strCommandText` 會表示要搜尋的目錄；它包含了命令物件的 `ICommandText` 介面所表示的文字。  如果沒有指定任何目錄，它會使用目前的目錄。  
  
 這種方法可以為每個檔案建立項目 \(對應至一資料列\)，並將它放在 **m\_rgRowData** 資料成員內。  `CRowsetImpl` 類別定義了 **m\_rgRowData** 資料成員。  這個陣列內的資料會表示整個資料表，且會套用於樣板內。  
  
## 請參閱  
 [提供者精靈產生的檔案](../../data/oledb/provider-wizard-generated-files.md)