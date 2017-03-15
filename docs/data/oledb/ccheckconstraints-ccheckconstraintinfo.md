---
title: "CCheckConstraints、CCheckConstraintInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CCheckConstraintInfo"
  - "CHECK_CONSTRAINTS"
  - "m_szCatalog"
  - "CCheckConstraints"
  - "CONSTRAINT_NAME"
  - "m_szSchema"
  - "CHECK_CLAUSE"
  - "m_szCheckClause"
  - "m_szName"
  - "CONSTRAINT_CATALOG"
  - "CONSTRAINT_SCHEMA"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCheckConstraintInfo 參數類別"
  - "CCheckConstraints typedef 類別"
  - "CHECK_CLAUSE"
  - "CHECK_CONSTRAINTS"
  - "CONSTRAINT_CATALOG"
  - "CONSTRAINT_NAME"
  - "CONSTRAINT_SCHEMA"
  - "DESCRIPTION 類別資料成員"
  - "m_szCatalog"
  - "m_szCheckClause"
  - "m_szDescription"
  - "m_szName"
  - "m_szSchema"
ms.assetid: e53e79a5-01e5-42b7-aa8c-164aec94b011
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CCheckConstraints、CCheckConstraintInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 typedef 類別 **CCheckConstraints** 實作它的參數類別 **CCheckConstraintInfo**。  
  
## 備註  
 請參閱 [結構描述資料列集類別及 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 。如需使用 typedef 類別的詳細資訊。  
  
 這個類別會識別檢查條件約束， \(定義在資料庫目錄中，由指定使用者所擁有。  檢查條件約束可指定在資料表中為一或多個資料行所接受的資料值或格式。  
  
 下表列出類別資料成員和其對應的 OLE DB 資料行。  請參閱《 *OLE DB 程式設計人員參考》的*[CHECK\_CONSTRAINTS 資料](https://msdn.microsoft.com/en-us/library/ms712845.aspx) 有關結構描述和資料列的詳細資訊。  
  
|資料成員|OLE DB 資料行|  
|----------|----------------|  
|m\_szCatalog|CONSTRAINT\_CATALOG|  
|m\_szSchema|CONSTRAINT\_SCHEMA|  
|m\_szName|CONSTRAINT\_NAME|  
|m\_szCheckClause|CHECK\_CLAUSE|  
|m\_szDescription|DESCRIPTION|  
  
## 需求  
 **Header:** atldbsch.h  
  
## 請參閱  
 [CRestrictions 類別](../../data/oledb/crestrictions-class.md)