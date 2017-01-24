---
title: "COLUMN_NAME_LENGTH | Microsoft Docs"
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
  - "COLUMN_NAME_LENGTH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_NAME_LENGTH 巨集"
ms.assetid: 3c4b6c94-d29d-4fba-a425-8186c9dc3f6a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COLUMN_NAME_LENGTH
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示資料列集至資料的特定資料行之繫結。  與 [COLUMN\_NAME](../../data/oledb/column-name.md) 類似，但是這個巨集也接受資料行長度。  
  
## 語法  
  
```  
  
COLUMN_NAME_LENGTH(  
pszName  
,   
data  
,   
length  
 )  
  
```  
  
#### 參數  
 `pszName`  
 \[in\] 指向資料欄名稱之指標。  名稱必須是 Unicode 字串。  您可以在名稱前加上一個「L」表示結束，例如： `L"MyColumn"`。  
  
 `data`  
 \[in\] 使用者資料記錄中對應的資料成員。  
  
 *length*  
 \[in\] 要繫結至資料行長度的變數。  
  
## 備註  
 如需 **COLUMN\_NAME\_\*** 巨集如何使用的相關資訊，請參閱 [COLUMN\_NAME](../../data/oledb/column-name.md)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN\_NAME](../../data/oledb/column-name.md)   
 [COLUMN\_NAME\_EX](../../data/oledb/column-name-ex.md)   
 [COLUMN\_NAME\_LENGTH\_STATUS](../../data/oledb/column-name-length-status.md)   
 [COLUMN\_NAME\_STATUS](../../data/oledb/column-name-status.md)   
 [COLUMN\_NAME\_PS](../../data/oledb/column-name-ps.md)   
 [COLUMN\_NAME\_PS\_LENGTH](../../data/oledb/column-name-ps-length.md)   
 [COLUMN\_NAME\_PS\_STATUS](../../data/oledb/column-name-ps-status.md)   
 [COLUMN\_NAME\_PS\_LENGTH\_STATUS](../../data/oledb/column-name-ps-length-status.md)   
 [COLUMN\_NAME\_TYPE](../../data/oledb/column-name-type.md)   
 [COLUMN\_NAME\_TYPE\_PS](../../data/oledb/column-name-type-ps.md)   
 [COLUMN\_NAME\_TYPE\_SIZE](../../data/oledb/column-name-type-size.md)   
 [COLUMN\_NAME\_TYPE\_STATUS](../../data/oledb/column-name-type-status.md)