---
title: "CViewTableUsage、CViewTableInfo | Microsoft Docs"
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
  - "m_szTableSchema"
  - "m_szCatalog"
  - "CViewTableInfo"
  - "m_szTableCatalog"
  - "m_szSchema"
  - "m_szTableName"
  - "m_szName"
  - "CViewTableUsage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CViewTableInfo 參數類別"
  - "CViewTableUsage typedef 類別"
  - "m_szCatalog"
  - "m_szName"
  - "m_szSchema"
  - "m_szTableCatalog"
  - "m_szTableName"
  - "m_szTableSchema"
  - "TABLE_CATALOG"
  - "TABLE_NAME"
  - "TABLE_SCHEMA"
ms.assetid: 10b74f2a-8010-4f97-acc2-ffce07349981
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CViewTableUsage、CViewTableInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 typedef 類別 **CViewTableUsage** 實作它的參數類別 **CViewTableInfo**。  
  
## 備註  
 如需使用 typedef 類別的詳細資訊，請參閱 [結構描述資料列集類別及 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 。  
  
 這個類別會識別為給定的使用者可在資料庫目錄中所定義的檢視表。  
  
 下表列出類別資料成員和其對應的 OLE DB 資料行。  有關結構描述和資料列的詳細資訊，請參閱 *OLE DB 程式設計人員參考資訊* 的 [VIEW\_TABLE\_USAGE Rowset](https://msdn.microsoft.com/en-us/library/ms719727.aspx)。  
  
|資料成員|OLE DB 資料行|  
|----------|----------------|  
|m\_szCatalog|VIEW\_CATALOG|  
|m\_szSchema|VIEW\_SCHEMA|  
|m\_szName|VIEW\_NAME|  
|m\_szTableCatalog|TABLE\_CATALOG|  
|m\_szTableSchema|TABLE\_SCHEMA|  
|m\_szTableName|TABLE\_NAME|  
  
## 需求  
 **標頭：** atldbsch.h  
  
## 請參閱  
 [CRestrictions 類別](../../data/oledb/crestrictions-class.md)