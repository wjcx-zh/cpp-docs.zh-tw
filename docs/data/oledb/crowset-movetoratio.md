---
title: "CRowset::MoveToRatio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MoveToRatio"
  - "CRowset<TAccessor>::MoveToRatio"
  - "CRowset::MoveToRatio"
  - "CRowset<TAccessor>.MoveToRatio"
  - "ATL.CRowset.MoveToRatio"
  - "ATL::CRowset::MoveToRatio"
  - "CRowset.MoveToRatio"
  - "ATL.CRowset<TAccessor>.MoveToRatio"
  - "ATL::CRowset<TAccessor>::MoveToRatio"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveToRatio 方法"
ms.assetid: 1fa313bd-8fd1-4608-8e85-44993b97dd88
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CRowset::MoveToRatio
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取在資料列集的分數位置開始資料列。  
  
## 語法  
  
```  
  
      HRESULT MoveToRatio(   
   DBCOUNTITEM nNumerator,   
   DBCOUNTITEM nDenominator,   
   bool bForward = true    
) throw( );  
```  
  
#### 參數  
 `nNumerator`  
 \[in\] 用於的分子判斷的分數位置擷取資料。  
  
 `nDenominator`  
 \[in\] 用於的分母判斷的分數位置擷取資料。  
  
 `bForward`  
 \[in\] 表示是否向前移動。  預設值為 forward。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 `MoveToRatio` 表示根據下列公式大致擷取資料行:  
  
 `( nNumerator *  RowsetSize ) / nDenominator`  
  
 其中 `RowsetSize` 是資料列的大小，以行來測量。  這個公式的精確度取決於特定提供者。  如需詳細資訊，請參閱 [IRowsetScroll::GetRowsAtRatio](https://msdn.microsoft.com/en-us/library/ms709602.aspx)。  
  
 這個方法要求選擇性 `IRowsetScroll` 介面，可能不是所有提供者都支援;如果是這種情況，方法會傳回 **E\_NOINTERFACE**。  在對資料表或是包含資料列集的命令呼叫 **Open** 之前您也必須設定 **DBPROP\_IRowsetScroll** 到 `VARIANT_TRUE`。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)