---
title: "CAssertions、CAssertionInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CAssertions"
  - "m_szCatalog"
  - "m_bInitiallyDeferred"
  - "CONSTRAINT_NAME"
  - "m_szSchema"
  - "INITIALLY_DEFERRED"
  - "m_bIsDeferrable"
  - "m_szName"
  - "CAssertionInfo"
  - "CONSTRAINT_CATALOG"
  - "CONSTRAINT_SCHEMA"
  - "IS_DEFERRABLE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAssertionInfo 參數類別"
  - "CAssertions typedef 類別"
  - "CONSTRAINT_CATALOG"
  - "CONSTRAINT_NAME"
  - "CONSTRAINT_SCHEMA"
  - "DESCRIPTION 類別資料成員"
  - "INITIALLY_DEFERRED"
  - "IS_DEFERRABLE"
  - "m_bInitiallyDeferred"
  - "m_bIsDeferrable"
  - "m_szCatalog"
  - "m_szDescription"
  - "m_szName"
  - "m_szSchema"
ms.assetid: 2a79c2da-5c9b-4fa6-98e8-90b7f5d6f021
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CAssertions、CAssertionInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 typedef 類別 **CAssertions** 實作它的參數類別 **CAssertionInfo**。  
  
## 備註  
 如需使用 typedef 類別的詳細資訊，請參閱 [結構描述資料列集類別及 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 。  
  
 這個類別會識別定義在由指定使用者所擁有的資料庫目錄中的聲明。  
  
 下表列出 **CAssertionInfo** 和其對應的 OLE DB 資料類別的資料成員。  如需有關結構描述和資料列的詳細資訊，請參閱《 *OLE DB 程式設計人員參考*》的[ASSERTIONS Rowset](https://msdn.microsoft.com/en-us/library/ms719776.aspx) 。  
  
|資料成員|OLE DB 資料行|  
|----------|----------------|  
|m\_szCatalog|CONSTRAINT\_CATALOG|  
|m\_szSchema|CONSTRAINT\_SCHEMA|  
|m\_szName|CONSTRAINT\_NAME|  
|m\_bIsDeferrable|IS\_DEFERRABLE|  
|m\_bInitiallyDeferred|INITIALLY\_DEFERRED|  
|m\_szDescription|DESCRIPTION|  
  
## 需求  
 **標頭：** atldbsch.h  
  
## 請參閱  
 [CRestrictions 類別](../../data/oledb/crestrictions-class.md)