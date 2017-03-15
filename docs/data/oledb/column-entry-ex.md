---
title: "COLUMN_ENTRY_EX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COLUMN_ENTRY_EX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_ENTRY_EX 巨集"
ms.assetid: dfad1b67-51c3-4289-b89a-da42d7e8bb88
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# COLUMN_ENTRY_EX
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示資料列集的繫結至資料庫中的特定行。  
  
## 語法  
  
```  
  
COLUMN_ENTRY_EX(  
nOrdinal  
,   
wType  
,   
nLength  
,   
nPrecision  
,   
nScale  
,   
data  
,   
length  
,   
status  
 )  
  
```  
  
#### 參數  
 請參閱《 *OLE DB 程式設計人員參考》的*[DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) 。  
  
 `nOrdinal`  
 \[的資料列數目。  
  
 `wType`  
 \[資料型別。  
  
 `nLength`  
 \[資料大小 \(以位元組為單位\)。  
  
 `nPrecision`  
 \[使用取得資料和 `wType` 時所使用的最大精確度是 `DBTYPE_NUMERIC`。  否則，會忽略這個參數。  
  
 `nScale`  
 \[使用取得資料和 `wType` 時要使用的小數位數是 `DBTYPE_NUMERIC` 或 **DBTYPE\_DECIMAL**。  
  
 `data`  
 \[使用者資料錄中對應的資料成員。  
  
 *length*  
 \[\] 將繫結的變數對資料行長度。  
  
 *status*  
 \[\] 將繫結的變數資料列狀態。  
  
## 備註  
 `COLUMN_ENTRY_EX` 巨集可在下列位置:  
  
-   在 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md) 和 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md) 巨集之間。  
  
-   在 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md) 和 [END\_ACCESSOR](../../data/oledb/end-accessor.md) 巨集之間。  
  
-   在 [BEGIN\_PARAM\_MAP](../../data/oledb/begin-param-map.md) 和 [END\_PARAM\_MAP](../../data/oledb/end-param-map.md) 巨集之間。  
  
## 範例  
 請參閱 [BOOKMARK\_ENTRY](../../data/oledb/bookmark-entry.md)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN\_ENTRY](../../data/oledb/column-entry.md)   
 [COLUMN\_ENTRY\_PS](../../data/oledb/column-entry-ps.md)   
 [COLUMN\_ENTRY\_PS\_LENGTH](../../data/oledb/column-entry-ps-length.md)   
 [COLUMN\_ENTRY\_LENGTH](../../data/oledb/column-entry-length.md)   
 [COLUMN\_ENTRY\_LENGTH\_STATUS](../../data/oledb/column-entry-length-status.md)   
 [COLUMN\_ENTRY\_PS\_LENGTH\_STATUS](../../data/oledb/column-entry-ps-length-status.md)   
 [COLUMN\_ENTRY\_STATUS](../../data/oledb/column-entry-status.md)   
 [COLUMN\_ENTRY\_PS\_STATUS](../../data/oledb/column-entry-ps-status.md)   
 [END\_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)