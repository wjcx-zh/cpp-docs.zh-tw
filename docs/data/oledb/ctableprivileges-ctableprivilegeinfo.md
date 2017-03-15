---
title: "CTablePrivileges、CTablePrivilegeInfo | Microsoft Docs"
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
  - "m_szCatalog"
  - "m_bIsGrantable"
  - "IS_GRANTABLE"
  - "m_szType"
  - "m_szSchema"
  - "m_szGrantor"
  - "GRANTOR"
  - "GRANTEE"
  - "CTablePrivileges"
  - "CTablePrivilegeInfo"
  - "m_szName"
  - "m_szGrantee"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTablePrivilegeInfo 參數類別"
  - "CTablePrivileges typedef 類別"
  - "GRANTEE"
  - "GRANTOR"
  - "IS_GRANTABLE"
  - "m_bIsGrantable"
  - "m_szCatalog"
  - "m_szGrantee"
  - "m_szGrantor"
  - "m_szName"
  - "m_szSchema"
  - "m_szType"
  - "TABLE_CATALOG"
  - "TABLE_NAME"
  - "TABLE_SCHEMA"
ms.assetid: ffcd6f73-022e-452a-8342-f2b9362d256b
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTablePrivileges、CTablePrivilegeInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 typedef 類別 **CTablePrivileges** 實作它的參數類別 **CTablePrivilegeInfo**。  
  
## 備註  
 請參閱 [結構描述資料列集類別及 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 。如需使用 typedef 類別的詳細資訊。  
  
 在目錄識別為指定使用者可以存取的資料表定義的類別。  
  
 下表列出類別資料成員和其對應的 OLE DB 資料行。  請參閱《 *OLE DB 程式設計人員參考》的*[TABLE\_PRIVILEGES 資料](https://msdn.microsoft.com/en-us/library/ms725428.aspx) 有關結構描述和資料列的詳細資訊。  
  
|資料成員|OLE DB 資料行|  
|----------|----------------|  
|m\_szGrantor|GRANTOR|  
|m\_szGrantee|GRANTEE|  
|m\_szCatalog|TABLE\_CATALOG|  
|m\_szSchema|TABLE\_SCHEMA|  
|m\_szName|TABLE\_NAME|  
|m\_szType|PRIVILEGE\_TYPE|  
|m\_bIsGrantable|IS\_GRANTABLE|  
  
## 需求  
 **Header:** atldbsch.h  
  
## 請參閱  
 [CRestrictions 類別](../../data/oledb/crestrictions-class.md)