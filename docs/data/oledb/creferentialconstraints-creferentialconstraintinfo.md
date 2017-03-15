---
title: "CReferentialConstraints、CReferentialConstraintInfo | Microsoft Docs"
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
  - "m_szUniqueName"
  - "m_szCatalog"
  - "DELETE_RULE"
  - "m_szUniqueCatalog"
  - "CONSTRAINT_NAME"
  - "CReferentialConstraintInfo"
  - "MATCH_OPTION"
  - "m_szSchema"
  - "m_szDeleteRule"
  - "m_szUpdateRule"
  - "m_szUniqueSchema"
  - "CReferentialConstraints"
  - "m_szName"
  - "CONSTRAINT_CATALOG"
  - "m_szMatchOption"
  - "CONSTRAINT_SCHEMA"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CONSTRAINT_CATALOG"
  - "CONSTRAINT_NAME"
  - "CONSTRAINT_SCHEMA"
  - "CReferentialConstraintInfo 參數類別"
  - "CReferentialConstraints typedef 類別"
  - "DELETE_RULE"
  - "DESCRIPTION 類別資料成員"
  - "m_szCatalog"
  - "m_szDeleteRule"
  - "m_szDescription"
  - "m_szMatchOption"
  - "m_szName"
  - "m_szSchema"
  - "m_szUniqueCatalog"
  - "m_szUniqueName"
  - "m_szUniqueSchema"
  - "m_szUpdateRule"
  - "MATCH_OPTION"
ms.assetid: 5d485358-be29-41c2-b0ce-19e023598e73
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CReferentialConstraints、CReferentialConstraintInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 typedef 類別 **CReferentialConstraints** 實作它的參數類別 **CReferentialConstraintInfo**。  
  
## 備註  
 如需使用 typedef 類別的詳細資訊，請參閱 [結構描述資料列集類別及 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 。  
  
 這個類別會識別定義在由指定使用者所擁有的資料庫目錄中的參考條件約束。  
  
 下表列出類別資料成員和其對應的 OLE DB 資料行。  有關結構描述和資料列的詳細資訊請參閱《 *OLE DB 程式設計人員參考*》的[REFERENTIAL\_CONSTRAINTS Rowset](https://msdn.microsoft.com/en-us/library/ms719737.aspx)。  
  
|資料成員|OLE DB 資料行|  
|----------|----------------|  
|m\_szCatalog|CONSTRAINT\_CATALOG|  
|m\_szSchema|CONSTRAINT\_SCHEMA|  
|m\_szName|CONSTRAINT\_NAME|  
|m\_szUniqueCatalog|UNIQUE\_CONSTRAINT\_CATALOG|  
|m\_szUniqueSchema|UNIQUE\_CONSTRAINT\_SCHEMA|  
|m\_szUniqueName|UNIQUE\_CONSTRAINT\_NAME|  
|m\_szMatchOption|MATCH\_OPTION|  
|m\_szUpdateRule|UPDATE RULE|  
|m\_szDeleteRule|DELETE\_RULE|  
|m\_szDescription|DESCRIPTION|  
  
## 需求  
 **標頭：** atldbsch.h  
  
## 請參閱  
 [CRestrictions 類別](../../data/oledb/crestrictions-class.md)