---
title: "PROVIDER_COLUMN_ENTRY_FIXED | Microsoft Docs"
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
  - "PROVIDER_COLUMN_ENTRY_FIXED"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROVIDER_COLUMN_ENTRY_FIXED 巨集"
ms.assetid: 71f9c9aa-56a0-488b-96ba-5c72da9c71d0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# PROVIDER_COLUMN_ENTRY_FIXED
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示提供者支援的特定資料行。  
  
## 語法  
  
```  
  
PROVIDER_COLUMN_ENTRY_FIXED(  
name  
, ordinal, dbtype, member )  
```  
  
#### 參數  
 *name*  
 \[in\] 資料行名稱。  
  
 `ordinal`  
 \[in\]資料行編號。  除非資料行是書籤資料行，不然不能為 0。  
  
 `dbtype`  
 \[in\] [DBTYPE](https://msdn.microsoft.com/en-us/library/ms711251.aspx)中的資料型別。  
  
 `member`  
 \[in\] 將資料儲存在 `dataClass` 的成員變數。  
  
## 備註  
 可讓您指定資料行的資料型別。  
  
## 範例  
 請參閱 [BEGIN\_PROVIDER\_COLUMN\_MAP](../../data/oledb/begin-provider-column-map.md)。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)