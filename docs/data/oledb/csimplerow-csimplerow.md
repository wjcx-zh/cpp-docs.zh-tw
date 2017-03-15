---
title: "CSimpleRow::CSimpleRow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CSimpleRow"
  - "ATL::CSimpleRow::CSimpleRow"
  - "CSimpleRow.CSimpleRow"
  - "ATL.CSimpleRow.CSimpleRow"
  - "CSimpleRow::CSimpleRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleRow 類別, 建構函式"
ms.assetid: 3968a36c-b8bb-48df-bd06-3956e64b0842
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CSimpleRow::CSimpleRow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建構函式。  
  
## 語法  
  
```  
  
      CSimpleRow(  
   DBCOUNTITEM iRowsetCur   
);  
```  
  
#### 參數  
 `iRowsetCur`  
 \[in\] 對目前資料列集的索引。  
  
## 備註  
 設定 [m\_iRowset](../../data/oledb/csimplerow-m-irowset.md) 為 `iRowsetCur`。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [CSimpleRow 類別](../../data/oledb/csimplerow-class.md)