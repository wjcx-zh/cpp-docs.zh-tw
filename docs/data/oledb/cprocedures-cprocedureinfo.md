---
title: "CProcedures、CProcedureInfo | Microsoft Docs"
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
  - "CProcedures"
  - "m_szCatalog"
  - "CProcedureInfo"
  - "m_szSchema"
  - "m_szDefinition"
  - "m_szName"
  - "m_nType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CProcedureInfo 參數類別"
  - "CProcedures typedef 類別"
  - "DESCRIPTION 類別資料成員"
  - "m_nType"
  - "m_szCatalog"
  - "m_szDefinition"
  - "m_szDescription"
  - "m_szName"
  - "m_szSchema"
ms.assetid: d0c7375e-ee0c-441d-aae6-6108150860a0
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CProcedures、CProcedureInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 typedef 類別 **CProcedures** 實作它的參數類別 **CProcedureInfo**。  
  
## 備註  
 請參閱 [結構描述資料列集類別及 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 。如需使用 typedef 類別的詳細資訊。  
  
 這個類別會識別程式， \(定義在資料庫目錄中，由指定使用者所擁有。  
  
 下表列出類別資料成員和其對應的 OLE DB 資料行。  請參閱《 *OLE DB 程式設計人員參考》的*[資料列集程序](https://msdn.microsoft.com/en-us/library/ms724021.aspx) 有關結構描述和資料列的詳細資訊。  
  
|資料成員|OLE DB 資料行|  
|----------|----------------|  
|m\_szCatalog|PROCEDURE\_CATALOG|  
|m\_szSchema|PROCEDURE\_SCHEMA|  
|m\_szName|PROCEDURE\_NAME|  
|m\_nType|PROCEDURE\_TYPE|  
|m\_szDefinition|PROCEDURE\_DEFINITION|  
|m\_szDescription|DESCRIPTION|  
  
## 需求  
 **Header:** atldbsch.h  
  
## 請參閱  
 [CRestrictions 類別](../../data/oledb/crestrictions-class.md)