---
title: "PROVIDER_COLUMN_ENTRY_LENGTH | Microsoft Docs"
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
  - "PROVIDER_COLUMN_ENTRY_LENGTH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROVIDER_COLUMN_ENTRY_LENGTH 巨集"
ms.assetid: b4a67246-c049-4622-bb65-242cc8cae4be
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# PROVIDER_COLUMN_ENTRY_LENGTH
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示提供者支援的特定資料行。  
  
## 語法  
  
```  
  
PROVIDER_COLUMN_ENTRY_LENGTH(  
name  
, ordinal, size, member )  
```  
  
#### 參數  
 *name*  
 \[資料行名稱。  
  
 `ordinal`  
 \[的資料列數目。  除非資料行是書籤資料行，不能為 0。  
  
 `size`  
 \[資料列大小 \(以位元組為單位\)。  
  
 `member`  
 \[儲存資料列資料為 `dataClass` 的成員變數。  
  
## 備註  
 可讓您指定資料列的大小。  
  
## 範例  
 請參閱 [BEGIN\_PROVIDER\_COLUMN\_MAP](../../data/oledb/begin-provider-column-map.md)。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)