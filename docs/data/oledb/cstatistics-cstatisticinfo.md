---
title: "CStatistics、CStatisticInfo | Microsoft Docs"
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
  - "CStatistics"
  - "m_szTableSchema"
  - "CStatisticInfo"
  - "m_szTableCatalog"
  - "m_nCardinality"
  - "m_szTableName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStatisticInfo 參數類別"
  - "CStatistics typedef 類別"
  - "m_nCardinality"
  - "m_szTableCatalog"
  - "m_szTableName"
  - "m_szTableSchema"
  - "TABLE_CATALOG"
  - "TABLE_NAME"
  - "TABLE_SCHEMA"
ms.assetid: 5822231c-6963-44a6-ae2f-29aca76e1600
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStatistics、CStatisticInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 typedef 類別 **CStatistics** 實作它的參數類別 **CStatisticInfo**。  
  
## 備註  
 如需使用 typedef 類別的詳細資訊，請參閱 [結構描述資料列集類別及 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 。  
  
 這個類別會識別定義在由指定使用者所擁有的資料庫目錄中的統計。  
  
 下表列出類別資料成員和其對應的 OLE DB 資料行。  如需有關結構描述和資料列的詳細資訊，請參閱*OLE DB 程式設計人員參考*的[STATISTICS Rowset](https://msdn.microsoft.com/en-us/library/ms715957.aspx) 。  
  
|資料成員|OLE DB 資料行|  
|----------|----------------|  
|m\_szTableCatalog|TABLE\_CATALOG|  
|m\_szTableSchema|TABLE\_SCHEMA|  
|m\_szTableName|TABLE\_NAME|  
|m\_nCardinality|CARDINALITY|  
  
## 需求  
 **標頭：** atldbsch.h  
  
## 請參閱  
 [CRestrictions 類別](../../data/oledb/crestrictions-class.md)