---
title: "CTranslations、CTranslationInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "m_szCatalog"
  - "m_szSourceCatalog"
  - "m_szTargetSchema"
  - "m_szTargetCatalog"
  - "m_szTargetName"
  - "CTranslationInfo"
  - "m_szSourceName"
  - "m_szSchema"
  - "CTranslations"
  - "m_szName"
  - "m_szSourceSchema"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTranslationInfo 參數類別"
  - "CTranslations typedef 類別"
  - "m_szCatalog"
  - "m_szName"
  - "m_szSchema"
  - "m_szSourceCatalog"
  - "m_szSourceName"
  - "m_szSourceSchema"
  - "m_szTargetCatalog"
  - "m_szTargetName"
  - "m_szTargetSchema"
ms.assetid: 19a64828-2d4c-42a0-8bfb-b010e334a9b3
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# CTranslations、CTranslationInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 typedef 類別 **CTranslations** 實作它的參數類別 **CTranslationInfo**。  
  
## 備註  
 如需使用 typedef 類別的詳細資訊，請參閱 [結構描述資料列集類別及 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 。  
  
 這個類別會識別為給定的使用者可在資料庫目錄中所定義的字元轉譯。  
  
 下表列出類別資料成員和其對應的 OLE DB 資料行。  如需有關結構描述和資料列的詳細資訊，請參閱*OLE DB 程式設計人員參考* 的[TRANSLATIONS Rowset](https://msdn.microsoft.com/en-us/library/ms725365.aspx) 。  
  
|資料成員|OLE DB 資料行|  
|----------|----------------|  
|m\_szCatalog|TRANSLATION\_CATALOG|  
|m\_szSchema|TRANSLATION\_SCHEMA|  
|m\_szName|TRANSLATION\_NAME|  
|m\_szSourceCatalog|SOURCE\_CHARACTER\_SET\_CATALOG|  
|m\_szSourceSchema|SOURCE\_CHARACTER\_SET\_SCHEMA|  
|m\_szSourceName|SOURCE\_CHARACTER\_SET\_NAME|  
|m\_szTargetCatalog|TARGET\_CHARACTER\_SET\_CATALOG|  
|m\_szTargetSchema|TARGET\_CHARACTER\_SET\_SCHEMA|  
|m\_szTargetName|TARGET\_CHARACTER\_SET\_NAME|  
  
## 需求  
 **標頭：** atldbsch.h  
  
## 請參閱  
 [CatDB](../../top/visual-cpp-samples.md)   
 [CRestrictions 類別](../../data/oledb/crestrictions-class.md)