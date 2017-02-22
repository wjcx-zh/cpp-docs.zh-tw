---
title: "tiled_index 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp/Concurrency::tiled_index"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tiled_index 類別"
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# tiled_index 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

提供到 [tiled\_extent](../../../parallel/amp/reference/tiled-extent-class.md) 物件的索引。  這個類別具有存取相對於本機磚原點和相對於全域原點的項目屬性。  如需已劃分 Tile 空間的詳細資訊，請參閱[使用磚](../../../parallel/amp/using-tiles.md)。  
  
## 語法  
  
```  
template <  
   int _Dim0,  
   int _Dim1 = 0,  
   int _Dim2 = 0  
>  
class tiled_index : public _Tiled_index_base<3>;  
  
template <  
   int _Dim0,  
   int _Dim1  
>  
class tiled_index<_Dim0, _Dim1, 0> : public _Tiled_index_base<2>;  
  
template <  
   int _Dim0  
>  
class tiled_index<_Dim0, 0, 0> : public _Tiled_index_base<1>;  
```  
  
#### 參數  
 `_Dim0`  
 最高有效維度的長度。  
  
 `_Dim1`  
 次高有效維度的長度。  
  
 `_Dim2`  
 最低有效維度的長度。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[tiled\_index::tiled\_index 建構函式](../Topic/tiled_index::tiled_index%20Constructor.md)|初始化 `tile_index` 類別的新執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[tiled\_index::get\_tile\_extent 方法](../Topic/tiled_index::get_tile_extent%20Method.md)|回傳一個具有 [tiled\_index](../../../parallel/amp/reference/tiled-index-class.md) 樣板引數 `_Dim0` 、 `_Dim1` 和 `_Dim2` 值的 [extent](../../../parallel/amp/reference/extent-class-cpp-amp.md) 物件。|  
  
### 公用常數  
  
|名稱|描述|  
|--------|--------|  
|[tiled\_index::barrier 常數](../Topic/tiled_index::barrier%20Constant.md)|儲存 [tile\_barrier](../../../parallel/amp/reference/tile-barrier-class.md) 物件，這個物件表示執行緒之目前磚中的屏障。|  
|||  
|[tiled\_index::global 常數](../Topic/tiled_index::global%20Constant.md)|儲存順位為 1、2 或 3 的 [index](../../../parallel/amp/reference/index-class.md) 物件，這個物件表示 [grid](http://msdn.microsoft.com/zh-tw/f7d1b6a6-586c-4345-b09a-bfc26c492cb0) 物件中的全域索引。|  
|[tiled\_index::local 常數](../Topic/tiled_index::local%20Constant.md)|儲存順位為 1、2 或 3 的 `index` 物件，這個物件表示 [tiled\_extent](../../../parallel/amp/reference/tiled-extent-class.md) 物件之目前磚中的相對索引。|  
|[tiled\_index::rank 常數](../Topic/tiled_index::rank%20Constant.md)|儲存 [tiled\_index](../../../parallel/amp/reference/tiled-index-class.md) 物件的順位。|  
|[tiled\_index::tile 常數](../Topic/tiled_index::tile%20Constant.md)|儲存順位為 1、2 或 3 的 `index` 物件，這個物件表示 `tiled_extent` 物件之目前磚的座標。|  
|[tiled\_index::tile\_dim0 常數](../Topic/tiled_index::tile_dim0%20Constant.md)|儲存最高有效維度的長度。|  
|[tiled\_index::tile\_dim1 常數](../Topic/tiled_index::tile_dim1%20Constant.md)|儲存次高有效維度的長度。|  
|[tiled\_index::tile\_dim2 常數](../Topic/tiled_index::tile_dim2%20Constant.md)|儲存最低有效維度的長度。|  
|[tiled\_index::tile\_origin 常數](../Topic/tiled_index::tile_origin%20Constant.md)|儲存順位為 1、2 或 3 的 `index` 物件，這個物件表示 `tiled_extent` 物件中目前磚之原點的全域座標。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[tiled\_index::tile\_extent 資料成員](../Topic/tiled_index::tile_extent%20Data%20Member.md)|取得 [extent](../../../parallel/amp/reference/extent-class-cpp-amp.md) 物件，這個物件具有 [tiled\_index](../../../parallel/amp/reference/tiled-index-class.md) 樣板引數 [tiled\_index](../../../parallel/amp/reference/tiled-index-class.md) 樣板引數 `_Dim0`、`_Dim1` 和 `_Dim2` 的值。|  
  
## 繼承階層架構  
 `_Tiled_index_base`  
  
 `tiled_index`  
  
## 需求  
 **標頭：**amp.h  
  
 **命名空間：**並行  
  
## 請參閱  
 [Concurrency 命名空間 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)