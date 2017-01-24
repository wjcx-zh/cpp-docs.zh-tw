---
title: "CTable::Open | Microsoft Docs"
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
  - "ATL.CTable.Open"
  - "ATL::CTable::Open"
  - "CTable::Open"
  - "CTable.Open"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Open 方法"
ms.assetid: 5d006d95-74d7-4e2b-b243-a33bc53b5455
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTable::Open
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

開啟資料表。  
  
## 語法  
  
```  
  
      HRESULT Open(  
   const CSession& session,  
   LPCWSTR wszTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0  
) throw ( );  
HRESULT Open(  
   const CSession& session,  
   LPCSTR szTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0  
) throw ( );  
HRESULT Open(  
   const CSession& session,  
   DBID& dbid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0  
) throw ( );  
```  
  
#### 參數  
 `session`  
 \[in\] 資料表開啟的工作階段。  
  
 *wszTableName*  
 \[in\] 開啟的資料表名稱，以 Unicode 字串。  
  
 *szTableName*  
 \[in\] 開啟的資料表名稱，以 ANSI 字串。  
  
 *dbid*  
 \[in\] 要開啟的資料表之**DBID**。  
  
 *pPropSet*  
 \[in\] 物件陣列的指標包含設定的屬性和值的 [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 結構。  請參閱 *《 OLE DB 程式設計人員參考》*的[屬性集合和屬性群組](https://msdn.microsoft.com/en-us/library/ms713696.aspx) [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  NULL 的預設值沒有指定屬性。  
  
 `ulPropSets`  
 \[in\] [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 結構的數目傳入*pPropSet* 作為引數。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 如需詳細資訊，請參閱 *OLE DB Programmer's Reference* 中的 [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CTable 類別](../../data/oledb/ctable-class.md)