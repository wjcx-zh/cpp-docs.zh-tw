---
title: "CSession::Open | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CSession::Open"
  - "CSession::Open"
  - "CSession.Open"
  - "ATL.CSession.Open"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Open 方法"
ms.assetid: c2050c2c-9817-4857-be49-189f346968f6
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CSession::Open
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

啟動資料來源物件的新工作階段。  
  
## 語法  
  
```  
  
      HRESULT Open(  
   const CDataSource& ds,  
   DBPROPSET *pPropSet = NULL,  
   ULONG ulPropSets = 0  
) throw( );  
```  
  
#### 參數  
 `ds`  
 \[這個工作階段將舉行的資料來源。  
  
 *pPropSet*  
 \[物件陣列的指標包含屬性和值的 [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 結構會設定。  請參閱《 *OLE DB 程式設計人員參考》的*[屬性集合和屬性群組](https://msdn.microsoft.com/en-us/library/ms713696.aspx)[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `ulPropSets`  
 \[ [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 結構數目。 *pPropSet* 引數傳遞的。  
  
## 傳回值  
 標準 `HRESULT`。  
  
## 備註  
 您必須開啟資料來源物件使用 [CDataSource::Open](../../data/oledb/cdatasource-open.md) 再將它設定為 `CSession::Open`。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CSession 類別](../../data/oledb/csession-class.md)