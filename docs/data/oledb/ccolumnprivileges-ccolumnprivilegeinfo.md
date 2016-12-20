---
title: "CColumnPrivileges、CColumnPrivilegeInfo | Microsoft Docs"
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
  - "CColumnPrivileges"
  - "m_bIsGrantable"
  - "m_nColumnPropID"
  - "m_szPrivilegeType"
  - "COLUMN_GUID"
  - "IS_GRANTABLE"
  - "m_szColumnName"
  - "m_szTableCatalog"
  - "m_szGrantor"
  - "GRANTOR"
  - "GRANTEE"
  - "COLUMN_PROPID"
  - "m_guidColumn"
  - "COLUMN_PRIVILEGES"
  - "m_szTableName"
  - "CColumnPrivilegeInfo"
  - "m_szGrantee"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CColumnPrivilegeInfo 參數類別"
  - "CColumnPrivileges typedef 類別"
  - "COLUMN_GUID"
  - "COLUMN_NAME"
  - "COLUMN_PRIVILEGES"
  - "COLUMN_PROPID"
  - "GRANTEE"
  - "GRANTOR"
  - "IS_GRANTABLE"
  - "m_bIsGrantable"
  - "m_guidColumn"
  - "m_nColumnPropID"
  - "m_szColumnName"
  - "m_szGrantee"
  - "m_szGrantor"
  - "m_szPrivilegeType"
  - "m_szTableCatalog"
  - "m_szTableName"
  - "m_szTableSchema"
  - "TABLE_CATALOG"
  - "TABLE_NAME"
  - "TABLE_SCHEMA"
ms.assetid: 245df365-421f-43c6-9fcd-fb2197c871c6
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CColumnPrivileges、CColumnPrivilegeInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 typedef 類別 **CColumnPrivileges** 實作它的參數類別 **CColumnPrivilegeInfo**。  
  
## 備註  
 如需使用 typedef 類別的詳細資訊，請參閱 [結構描述資料列集類別及 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 。  
  
 此類別定義在資料庫目錄中所定義資料表之資料行上的權限；指定之使用者可以取得或授與這些權限。  
  
 下表列出類別資料成員和其對應的 OLE DB 資料行。  有關結構描述和資料列的詳細資訊請參閱《 *OLE DB 程式設計人員參考*》的[COLUMN\_PRIVILEGES](https://msdn.microsoft.com/en-us/library/ms715800.aspx) 。  
  
|資料成員|OLE DB 資料行|  
|----------|----------------|  
|m\_szGrantor|GRANTOR|  
|m\_szGrantee|GRANTEE|  
|m\_szTableCatalog|TABLE\_CATALOG|  
|m\_szTableSchema|TABLE\_SCHEMA|  
|m\_szTableName|TABLE\_NAME|  
|m\_szColumnName|COLUMN\_NAME|  
|m\_guidColumn|COLUMN\_GUID|  
|m\_nColumnPropID|COLUMN\_PROPID|  
|m\_szPrivilegeType|PRIVILEGE\_TYPE|  
|m\_bIsGrantable|IS\_GRANTABLE|  
  
## 需求  
 **標頭：** atldbsch.h  
  
## 請參閱  
 [CRestrictions 類別](../../data/oledb/crestrictions-class.md)