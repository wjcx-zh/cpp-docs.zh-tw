---
title: "CDataSource::Open | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CDataSource::Open"
  - "ATL.CDataSource.Open"
  - "CDataSource::Open"
  - "CDataSource.Open"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Open 方法"
ms.assetid: a6d28bd1-799a-48ed-8993-5f82d1705b77
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataSource::Open
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 **CLSID**、**ProgID** 或 `CEnumerator` Moniker 開啟資料來源的連接，或以定位程式對話方塊來提示使用者。  
  
## 語法  
  
```  
  
        HRESULT Open(  
   const CLSID& clsid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1   
) throw( );  
HRESULT Open(  
   const CLSID& clsid,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0   
) throw( );  
HRESULT Open(  
   LPCTSTR szProgID,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1   
) throw( );  
HRESULT Open(  
   LPCTSTR szProgID,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0   
) throw( );  
HRESULT Open(  
   const CEnumerator& enumerator,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1   
) throw( );  
HRESULT Open(  
   const CEnumerator& enumerator,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0   
) throw( );  
HRESULT Open(  
   HWND hWnd = GetActiveWindow( ),  
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_WIZARDSHEET   
) throw( );  
HRESULT Open(   
   LPCWSTR szProgID,   
   DBPROPSET* pPropSet = NULL,   
   ULONG nPropertySets = 1   
) throw( );  
HRESULT Open(   
   LPCSTR szProgID,   
   LPCTSTR pName,   
   LPCTSTR pUserName = NULL,   
   LPCTSTR pPassword = NULL,   
   long nInitMode = 0   
) throw( );  
```  
  
#### 參數  
 `clsid`  
 \[in\] 資料提供者的 **CLSID**。  
  
 *pPropSet*  
 \[in\] [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 結構陣列的指標，其中包含要設定的屬性和值。  請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 的《*OLE DB 程式設計人員參考*》中的[屬性集和屬性群組](https://msdn.microsoft.com/en-us/library/ms713696.aspx)。  
  
 *nPropertySets*  
 \[in\] 傳入 *pPropSet* 引數中的 [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 結構數目。  
  
 *pName*  
 \[in\] 要連接的資料庫名稱。  
  
 *pUserName*  
 \[in\] 使用者的名稱。  
  
 *pPassword*  
 \[in\] 使用者的密碼。  
  
 `nInitMode`  
 \[in\] 資料庫初始化模式。  如需有效初始化模式的清單，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 的《*OLE DB 程式設計人員參考*》中的[初始化屬性](https://msdn.microsoft.com/en-us/library/ms723127.aspx)。  如果 `nInitMode` 是零，則用來開啟連接的屬性集不包含任何初始化模式。  
  
 `szProgID`  
 \[in\] 程式識別碼。  
  
 `enumerator`  
 \[in\] [CEnumerator](../../data/oledb/cenumerator-class.md) 物件，用來取得 Moniker，以便呼叫端未指定 **CLSID** 時開啟連接。  
  
 `hWnd`  
 \[in\] 做為對話方塊之父視窗的控制代碼。  如果使用的函式多載用到 `hWnd` 參數，將會自動叫用服務元件。如需詳細資訊，請參閱＜備註＞。  
  
 `dwPromptOptions`  
 \[in\] 決定要顯示的定位程式對話方塊樣式。  請參閱 Msdasc.h 中的可能值。  
  
## 傳回值  
 標準 `HRESULT`。  
  
## 備註  
 如果方法多載使用 `hWnd` 參數，則會使用 oledb32.dll 中的服務元件開啟資料來源物件。此 DLL 包含服務元件功能的實作，例如資源共用、自動交易登記等。  如需詳細資訊，請參閱《OLE DB 程式設計人員參考》中的＜OLE DB 服務＞：[http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/oledb\/htm\/oledbole\_db\_services.asp?frame\=true](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)。  
  
 如果方法多載未使用 `hWnd` 參數，則會在不使用 oledb32.dll 中的服務元件的情況下開啟資料來源物件。  使用這些函式多載開啟的 [CDataSource](../../data/oledb/cdatasource-class.md) 物件，將無法利用服務元件的任何功能。  
  
## 範例  
 下列程式碼示範如何使用 OLE DB 範本開啟 Jet 4.0 資料來源。  您可以將 Jet 資料來源當做 OLE DB 資料來源。  不過，呼叫 **Open** 需要兩個屬性集：一個用於 **DBPROPSET\_DBINIT**，另一個用於 **DBPROPSET\_JETOLEDB\_DBINIT**，如此您可以設定 **DBPROP\_JETOLEDB\_DATABASEPASSWORD**。  
  
 [!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/CPP/cdatasource-open_1.cpp)]  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDataSource 類別](../../data/oledb/cdatasource-class.md)