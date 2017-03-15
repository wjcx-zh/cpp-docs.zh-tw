---
title: "COLUMN_ENTRY_PS_LENGTH | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COLUMN_ENTRY_PS_LENGTH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_ENTRY_PS_LENGTH 巨集"
ms.assetid: d63ab895-a4df-4183-ac09-cf2311222408
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# COLUMN_ENTRY_PS_LENGTH
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示資料列集的繫結至資料庫中的特定行。  
  
## 語法  
  
```  
  
COLUMN_ENTRY_PS_LENGTH(  
nOrdinal  
,   
nPrecision  
,   
nScale  
,   
data  
,   
length  
 )  
  
```  
  
#### 參數  
 請參閱《 *OLE DB 程式設計人員參考》的*[DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) 。  
  
 `nOrdinal`  
 \[行數，是從一開始。  將書籤資料行零。  
  
 `nPrecision`  
 \[要繫結之資料行的最大精確度。  
  
 `nScale`  
 \[要繫結之資料行的比例。  
  
 `data`  
 \[使用者資料錄中對應的資料成員。  
  
 *length*  
 \[\] 將繫結的變數對資料行長度。  
  
## 備註  
 可讓您指定要繫結資料行的精確度和小數位數。  這個巨集支援長度變數。  在下列位置:  
  
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
 [COLUMN\_ENTRY\_LENGTH\_STATUS](../../data/oledb/column-entry-length-status.md)   
 [COLUMN\_ENTRY\_PS\_LENGTH\_STATUS](../../data/oledb/column-entry-ps-length-status.md)   
 [COLUMN\_ENTRY\_STATUS](../../data/oledb/column-entry-status.md)   
 [COLUMN\_ENTRY\_PS\_STATUS](../../data/oledb/column-entry-ps-status.md)   
 [END\_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)