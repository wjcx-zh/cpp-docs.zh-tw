---
title: "CCollations、CCollationInfo | Microsoft Docs"
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
  - "COLLATION_CATALOG"
  - "m_szCatalog"
  - "CCollationInfo"
  - "CCollations"
  - "CHARACTER_SET_NAME"
  - "CHARACTER_SET_SCHEMA"
  - "m_szCharSetName"
  - "m_szSchema"
  - "CHARACTER_SET_CATALOG"
  - "m_szCharSetSchema"
  - "m_szCharSetCatalog"
  - "m_szPadAttribute"
  - "COLLATION_NAME"
  - "COLLATION_SCHEMA"
  - "m_szName"
  - "COLLATIONS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCollationInfo 參數類別"
  - "CCollations typedef 類別"
  - "CHARACTER_SET_CATALOG"
  - "CHARACTER_SET_NAME"
  - "CHARACTER_SET_SCHEMA"
  - "COLLATION_CATALOG"
  - "COLLATION_NAME"
  - "COLLATION_SCHEMA"
  - "COLLATIONS 資料錄集"
  - "m_szCatalog"
  - "m_szCharSetCatalog"
  - "m_szCharSetName"
  - "m_szCharSetSchema"
  - "m_szName"
  - "m_szPadAttribute"
  - "m_szSchema"
ms.assetid: d8b43c4d-9dd5-4043-b4c8-38c03bfa0c72
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCollations、CCollationInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 typedef 類別 **CCollations** 實作它的參數類別 **CCollationInfo**。  
  
## 備註  
 請參閱 [結構描述資料列集類別及 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 。如需使用 typedef 類別的詳細資訊。  
  
 這個類別會識別字元順序， \(定義在資料庫目錄中，由指定使用者進行存取。  
  
 下表列出類別資料成員和其對應的 OLE DB 資料行。  請參閱《 *OLE DB 程式設計人員參考》的*[排序資料](https://msdn.microsoft.com/en-us/library/ms715783.aspx) 有關結構描述和資料列的詳細資訊。  
  
|資料成員|OLE DB 資料行|  
|----------|----------------|  
|m\_szCatalog|COLLATION\_CATALOG|  
|m\_szSchema|COLLATION\_SCHEMA|  
|m\_szName|COLLATION\_NAME|  
|m\_szCharSetCatalog|CHARACTER\_SET\_CATALOG|  
|m\_szCharSetSchema|CHARACTER\_SET\_SCHEMA|  
|m\_szCharSetName|CHARACTER\_SET\_NAME|  
|m\_szPadAttribute|PAD\_ATTRIBUTE|  
  
## 需求  
 **Header:** atldbsch.h  
  
## 請參閱  
 [CRestrictions 類別](../../data/oledb/crestrictions-class.md)