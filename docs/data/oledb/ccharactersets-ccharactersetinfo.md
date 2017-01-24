---
title: "CCharacterSets、CCharacterSetInfo | Microsoft Docs"
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
  - "m_szCollateName"
  - "m_szCatalog"
  - "DEFAULT_COLLATE_NAME"
  - "m_szCollateSchema"
  - "FORM_OF_USE"
  - "DEFAULT_COLLATE_SCHEMA"
  - "m_szCollateCatalog"
  - "CCharacterSets"
  - "CHARACTER_SET_NAME"
  - "DEFAULT_COLLATE_CATALOG"
  - "CHARACTER_SET_SCHEMA"
  - "m_szFormOfUse"
  - "NUMBER_OF_CHARACTERS"
  - "m_szSchema"
  - "CHARACTER_SET_CATALOG"
  - "CCharacterSetInfo"
  - "m_nNumCharacters"
  - "m_szName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCharacterSetInfo 參數類別"
  - "CCharacterSets typedef 類別"
  - "CHARACTER_SET_CATALOG"
  - "CHARACTER_SET_NAME"
  - "CHARACTER_SET_SCHEMA"
  - "DEFAULT_COLLATE_CATALOG"
  - "DEFAULT_COLLATE_NAME"
  - "DEFAULT_COLLATE_SCHEMA"
  - "FORM_OF_USE OLE DB 資料行"
  - "m_nNumCharacters"
  - "m_szCatalog"
  - "m_szCollateCatalog"
  - "m_szCollateName"
  - "m_szCollateSchema"
  - "m_szFormOfUse"
  - "m_szName"
  - "m_szSchema"
  - "NUMBER_OF_CHARACTERS"
ms.assetid: 029d068c-8bb2-4fc0-8709-78ce7f74446e
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCharacterSets、CCharacterSetInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 typedef 類別 **CCharacterSets** 實作它的參數類別 **CCharacterSetInfo**。  
  
## 備註  
 如需使用 typedef 類別的詳細資訊，請參閱 [結構描述資料列集類別及 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 。  
  
 這個類別會識別為給定的使用者可在資料庫目錄中所定義的字元集。  
  
 下表列出類別資料成員和其對應的 OLE DB 資料行。  如需有關結構描述和資料列的詳細資訊，請參閱《 *OLE DB 程式設計人員參考*》的[CHARACTER\_SETS Rowset](https://msdn.microsoft.com/en-us/library/ms722638.aspx) 。  
  
|資料成員|OLE DB 資料行|  
|----------|----------------|  
|m\_szCatalog|CHARACTER\_SET\_CATALOG|  
|m\_szSchema|CHARACTER\_SET\_SCHEMA|  
|m\_szName|CHARACTER\_SET\_NAME|  
|m\_szFormOfUse|FORM\_OF\_USE|  
|m\_nNumCharacters|NUMBER\_OF\_CHARACTERS|  
|m\_szCollateCatalog|DEFAULT\_COLLATE\_CATALOG|  
|m\_szCollateSchema|DEFAULT\_COLLATE\_SCHEMA|  
|m\_szCollateName|DEFAULT\_COLLATE\_NAME|  
  
## 需求  
 **標頭：** atldbsch.h  
  
## 請參閱  
 [CRestrictions 類別](../../data/oledb/crestrictions-class.md)