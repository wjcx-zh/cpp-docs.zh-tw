---
title: "CDataSource::OpenWithServiceComponents | Microsoft Docs"
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
  - "CDataSource::OpenWithServiceComponents"
  - "OpenWithServiceComponents"
  - "CDataSource.OpenWithServiceComponents"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OpenWithServiceComponents 方法"
ms.assetid: 49c1d037-36ae-4fde-8e54-ced623abe1a9
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataSource::OpenWithServiceComponents
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 oledb32.dll 中的服務元件來開啟資料來源物件。  
  
## 語法  
  
```  
  
        HRESULT OpenWithServiceComponents (  
   const CLSID clsid,  
   DBPROPSET* pPropset = NULL,  
   ULONG ulPropSets = 1   
);  
HRESULT OpenWithServiceComponents (  
   LPCSTR szProgID,  
   DBPROPSET* pPropset = NULL,  
   ULONG ulPropSets = 1   
);  
```  
  
#### 參數  
 `clsid`  
 \[in\] 資料提供者的 **CLSID**。  
  
 `szProgID`  
 \[in\] 資料提供者的程式識別碼。  
  
 `pPropset`  
 \[in\] [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 結構陣列的指標，其中包含要設定的屬性和值。  請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 的《*OLE DB 程式設計人員參考*》中的[屬性集和屬性群組](https://msdn.microsoft.com/en-us/library/ms713696.aspx)。  如果資料來源物件已初始化，屬性必須屬於資料來源屬性群組。  若在 `pPropset` 中指定相同的屬性多次，則使用的哪些值是提供者所特有的。  如果 `ulPropSets` 為零，會忽略這個參數。  
  
 `ulPropSets`  
 \[in\] 傳入 *pPropSet* 引數中的 [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 結構數目。  若是零，提供者會忽略 `pPropset`。  
  
## 傳回值  
 標準 `HRESULT`。  
  
## 備註  
 這個方法會使用 oledb32.dll 中的服務元件開啟資料來源物件；此 DLL 包含服務元件功能的實作，例如資源集中化、自動交易登記等。  如需詳細資訊，請參閱《OLE DB 程式設計人員參考》中的＜OLE DB 服務＞：[http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/oledb\/htm\/oledbole\_db\_services.asp?frame\=true](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDataSource 類別](../../data/oledb/cdatasource-class.md)