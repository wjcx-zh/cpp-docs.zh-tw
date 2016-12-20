---
title: "COLUMN_ENTRY_STATUS | Microsoft Docs"
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
  - "COLUMN_ENTRY_STATUS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_ENTRY_STATUS 巨集"
ms.assetid: 29ffe8b6-cb1e-438c-813e-2e6d73a5deef
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COLUMN_ENTRY_STATUS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示資料列集至資料庫的特定資料行之繫結。  
  
## 語法  
  
```  
  
COLUMN_ENTRY_STATUS(  
nOrdinal  
,   
data  
,   
status  
 )  
  
```  
  
#### 參數  
 請參閱 *OLE DB 程式設計人員參考* 中的 [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)。  
  
 `nOrdinal`  
 \[in\]資料行編號。  
  
 `data`  
 \[in\] 使用者資料錄中對應的資料成員。  
  
 *status*  
 \[in\] 要繫結至資料行狀態的變數。  
  
## 備註  
 這個巨集支援 *狀態* 變數。  這個參數可以用於下列狀況：  
  
-   在 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md) 和 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md) 巨集之間。  
  
-   在 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md) 和 [END\_ACCESSOR](../../data/oledb/end-accessor.md) 巨集之間。  
  
-   在 [BEGIN\_PARAM\_MAP](../../data/oledb/begin-param-map.md) 和 [END\_PARAM\_MAP](../../data/oledb/end-param-map.md) 巨集之間。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN\_ENTRY](../../data/oledb/column-entry.md)   
 [COLUMN\_ENTRY\_EX](../../data/oledb/column-entry-ex.md)   
 [COLUMN\_ENTRY\_LENGTH](../../data/oledb/column-entry-length.md)   
 [COLUMN\_ENTRY\_PS](../../data/oledb/column-entry-ps.md)   
 [COLUMN\_ENTRY\_PS\_LENGTH](../../data/oledb/column-entry-ps-length.md)   
 [COLUMN\_ENTRY\_LENGTH\_STATUS](../../data/oledb/column-entry-length-status.md)   
 [COLUMN\_ENTRY\_PS\_LENGTH\_STATUS](../../data/oledb/column-entry-ps-length-status.md)   
 [COLUMN\_ENTRY\_PS\_STATUS](../../data/oledb/column-entry-ps-status.md)   
 [END\_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)