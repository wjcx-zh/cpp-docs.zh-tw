---
title: "PROVIDER_COLUMN_ENTRY_WSTR | Microsoft Docs"
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
  - "PROVIDER_COLUMN_ENTRY_WSTR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROVIDER_COLUMN_ENTRY_WSTR 巨集"
ms.assetid: 70630bd5-d782-473b-9777-aebbbf5321c5
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# PROVIDER_COLUMN_ENTRY_WSTR
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示提供者支援的特定資料行。  
  
## 語法  
  
```  
  
PROVIDER_COLUMN_ENTRY_WSTR(  
name  
, ordinal, member )  
```  
  
#### 參數  
 *name*  
 \[in\] 資料行名稱。  
  
 `ordinal`  
 \[in\]資料行編號。  除非資料行是書籤資料行，不然不能為 0。  
  
 `member`  
 \[in\] 資料類別中儲存資料的成員變數。  
  
## 備註  
 當資料是以 NULL 結束的 Unicode [DBTYPE\_WSTR](https://msdn.microsoft.com/en-us/library/ms711251.aspx) 字串時 ，使用這個巨集。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)