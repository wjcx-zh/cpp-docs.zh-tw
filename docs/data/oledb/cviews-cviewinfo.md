---
title: "CViews、CViewInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "m_szTableSchema"
  - "m_bCheckOption"
  - "CViews"
  - "CHECK_OPTION"
  - "CViewInfo"
  - "m_szTableCatalog"
  - "IS_UPDATABLE"
  - "m_szDefinition"
  - "m_szTableName"
  - "m_bIsUpdatable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHECK_OPTION"
  - "CViewInfo 參數類別"
  - "CViews typedef 類別"
  - "DESCRIPTION 類別資料成員"
  - "IS_UPDATABLE"
  - "m_bCheckOption"
  - "m_bIsUpdatable"
  - "m_szDefinition"
  - "m_szDescription"
  - "m_szTableCatalog"
  - "m_szTableName"
  - "m_szTableSchema"
  - "TABLE_CATALOG"
  - "TABLE_NAME"
  - "TABLE_SCHEMA"
ms.assetid: ad864181-4fab-4919-b0fd-45df5da230d9
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CViews、CViewInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 typedef 類別 **CViews** 以實作它的參數類別 **CViewInfo**。  
  
## 備註  
 如需使用 typedef 類別的詳細資訊，請參閱 [結構描述資料列集類別及 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 。  
  
 此類別會識別定義在由指定使用者所擁有資料庫目錄中的資料表，為相依的資料表。  
  
 下表列出類別資料成員和其對應的 OLE DB 資料行。  有關結構描述和資料列的詳細資訊請參閱《 *OLE DB 程式設計人員參考*》的[VIEWS Rowset](https://msdn.microsoft.com/en-us/library/ms723122.aspx)  
  
|資料成員|OLE DB 資料行|  
|----------|----------------|  
|m\_szTableCatalog|TABLE\_CATALOG|  
|m\_szTableSchema|TABLE\_SCHEMA|  
|m\_szTableName|TABLE\_NAME|  
|m\_szDefinition|VIEW\_DEFINITION|  
|m\_bCheckOption|CHECK\_OPTION|  
|m\_bIsUpdatable|IS\_UPDATABLE|  
|m\_szDescription|DESCRIPTION|  
  
## 需求  
 **標頭：** atldbsch.h  
  
## 請參閱  
 [CRestrictions 類別](../../data/oledb/crestrictions-class.md)