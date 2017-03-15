---
title: "COLUMN_NAME_LENGTH_STATUS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COLUMN_NAME_LENGTH_STATUS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_NAME_LENGTH_STATUS 巨集"
ms.assetid: f73bd592-7ca7-461c-b106-9a8b1adbb01e
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# COLUMN_NAME_LENGTH_STATUS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示資料列集的繫結至資料的特定資料行。  與 [COLUMN\_NAME](../../data/oledb/column-name.md)類似，但是有一點例外，就是這個巨集也會接受資料行長度和資料列狀態。  
  
## 語法  
  
```  
  
COLUMN_NAME_LENGTH_STATUS(  
pszName  
,   
data  
,   
length  
,   
status )  
```  
  
#### 參數  
 `pszName`  
 \[out 資料欄名稱之指標。  名稱必須是 Unicode 字串。  \(您可以將一個" L」完成此名稱前面，: `L"MyColumn"`。  
  
 `data`  
 \[使用者資料錄中對應的資料成員。  
  
 *length*  
 \[\] 將繫結的變數對資料行長度。  
  
 *status*  
 \[\] 將繫結的變數資料列狀態。  
  
## 備註  
 如需的相關資訊使用 **COLUMN\_NAME\_\*** 巨集中的 [COLUMN\_NAME](../../data/oledb/column-name.md) 參考。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN\_NAME](../../data/oledb/column-name.md)   
 [COLUMN\_NAME\_EX](../../data/oledb/column-name-ex.md)   
 [COLUMN\_NAME\_LENGTH](../../data/oledb/column-name-length.md)   
 [COLUMN\_NAME\_STATUS](../../data/oledb/column-name-status.md)   
 [COLUMN\_NAME\_PS](../../data/oledb/column-name-ps.md)   
 [COLUMN\_NAME\_PS\_LENGTH](../../data/oledb/column-name-ps-length.md)   
 [COLUMN\_NAME\_PS\_STATUS](../../data/oledb/column-name-ps-status.md)   
 [COLUMN\_NAME\_PS\_LENGTH\_STATUS](../../data/oledb/column-name-ps-length-status.md)   
 [COLUMN\_NAME\_TYPE](../../data/oledb/column-name-type.md)   
 [COLUMN\_NAME\_TYPE\_PS](../../data/oledb/column-name-type-ps.md)   
 [COLUMN\_NAME\_TYPE\_SIZE](../../data/oledb/column-name-type-size.md)   
 [COLUMN\_NAME\_TYPE\_STATUS](../../data/oledb/column-name-type-status.md)