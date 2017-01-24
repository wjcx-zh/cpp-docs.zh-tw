---
title: "CBulkRowset::MoveToRatio | Microsoft Docs"
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
  - "CBulkRowset.MoveToRatio"
  - "ATL::CBulkRowset::MoveToRatio"
  - "MoveToRatio"
  - "CBulkRowset::MoveToRatio"
  - "ATL.CBulkRowset<TAccessor>.MoveToRatio"
  - "ATL::CBulkRowset<TAccessor>::MoveToRatio"
  - "ATL.CBulkRowset.MoveToRatio"
  - "CBulkRowset<TAccessor>::MoveToRatio"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveToRatio 方法"
ms.assetid: 86be60f5-9341-44c1-8e1e-9174c082d0d5
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBulkRowset::MoveToRatio
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取在資料列集的分數位置開始資料列。  
  
## 語法  
  
```  
  
      HRESULT MoveToRatio(  
   DBCOUNTITEM nNumerator,  
   DBCOUNTITEM nDenominator   
) throw( );  
```  
  
#### 參數  
 `nNumerator`  
 \[in\] 用於的分子判斷的分數位置擷取資料。  
  
 `nDenominator`  
 \[in\] 用於的分母判斷的分數位置擷取資料。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 `MoveToRatio` 表示根據下列公式大致擷取資料行:  
  
 `( nNumerator *  RowsetSize ) / nDenominator`  
  
 其中 `RowsetSize` 是資料列的大小，以資料行。  這個公式的精確度取決於特定提供者。  如需詳細資訊，請參閱《 *OLE DB 程式設計人員參考》的*[IRowsetScroll::GetRowsAtRatio](https://msdn.microsoft.com/en-us/library/ms709602.aspx) 。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CBulkRowset 類別](../../data/oledb/cbulkrowset-class.md)