---
title: "CSchemata、CSchemataInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEFAULT_CHARACTER_SET_CATALOG"
  - "DEFAULT_CHARACTER_SET_SCHEMA"
  - "m_szCharName"
  - "CSchemataInfo"
  - "m_szCatalog"
  - "m_szCharCatalog"
  - "m_szOwner"
  - "m_szCharSchema"
  - "CSchemata"
  - "m_szName"
  - "DEFAULT_CHARACTER_SET_NAME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSchemata typedef 類別"
  - "CSchemataInfo 參數類別"
  - "DEFAULT_CHARACTER_SET_CATALOG"
  - "DEFAULT_CHARACTER_SET_NAME"
  - "DEFAULT_CHARACTER_SET_SCHEMA"
  - "m_szCatalog"
  - "m_szCharCatalog"
  - "m_szCharName"
  - "m_szCharSchema"
  - "m_szName"
  - "m_szOwner"
ms.assetid: 9d06d65a-c27b-446d-bc42-c7e487b0d9c5
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# CSchemata、CSchemataInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 typedef 類別 **CSchemata** 實作它的參數類別 **CSchemataInfo**。  
  
## 備註  
 如需使用 typedef 類別的詳細資訊，請參閱 [結構描述資料列集類別及 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 。  
  
 這個類別會識別由指定使用者所擁有的結構描述。  
  
 下表列出類別資料成員和其對應的 OLE DB 資料行。  如需有關結構描述和資料列的詳細資訊，請參閱*OLE DB 程式設計人員參考*的[SCHEMATA Rowset](https://msdn.microsoft.com/en-us/library/ms716887.aspx) 。  
  
|資料成員|OLE DB 資料行|  
|----------|----------------|  
|m\_szCatalog|CATALOG\_NAME|  
|m\_szName|SCHEMA\_NAME|  
|m\_szOwner|SCHEMA\_OWNER|  
|m\_szCharCatalog|DEFAULT\_CHARACTER\_SET\_CATALOG|  
|m\_szCharSchema|DEFAULT\_CHARACTER\_SET\_SCHEMA|  
|m\_szCharName|DEFAULT\_CHARACTER\_SET\_NAME|  
  
## 需求  
 **標頭：** atldbsch.h  
  
## 請參閱  
 [CRestrictions 類別](../../data/oledb/crestrictions-class.md)