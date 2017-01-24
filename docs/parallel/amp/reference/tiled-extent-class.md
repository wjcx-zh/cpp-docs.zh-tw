---
title: "tiled_extent 類別 | Microsoft Docs"
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
  - "amp/Concurrency::tiled_extent"
dev_langs: 
  - "C++"
ms.assetid: 671ecaf8-c7b0-4ac8-bbdc-e30bd92da7c0
caps.latest.revision: 9
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# tiled_extent 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`tiled_extent` 物件是有一至三個維度的 `extent` 物件，維度會將範圍空間劃分為一、二或三維的拼貼。  
  
## 語法  
  
```  
template <  
   int _Dim0,  
   int _Dim1,  
   int _Dim2  
>  
class tiled_extent : public Concurrency::extent<3>;  
  
template <  
   int _Dim0,  
   int _Dim1  
>  
class tiled_extent<_Dim0, _Dim1, 0> : public Concurrency::extent<2>;  
  
template <  
   int _Dim0  
>  
class tiled_extent<_Dim0, 0, 0> : public Concurrency::extent<1>;  
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
|[tiled\_extent::tiled\_extent 建構函式](../Topic/tiled_extent::tiled_extent%20Constructor.md)|初始化 `tiled_extent` 類別的新執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[tiled\_extent::get\_tile\_extent 方法](../Topic/tiled_extent::get_tile_extent%20Method.md)|傳回一個可以擷取以 `_Dim0` 、`_Dim1` 和 `_Dim2` 為引數的 `tiled_extent` 樣板的值的 `extent` 物件。|  
|[tiled\_extent::pad 方法](../Topic/tiled_extent::pad%20Method.md)|傳回一個向上調整為能被 tile 維度整除大小整除的範圍的 `tiled_extent` 物件。|  
|[tiled\_extent::truncate 方法](../Topic/tiled_extent::truncate%20Method.md)|傳回一個向下調整為能被 tile 維度整除大小整除的範圍的 `tiled_extent` 物件。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[tiled\_extent::operator\= 運算子](../Topic/tiled_extent::operator=%20Operator.md)|將指定之 `tiled_index` 物件的內容複製到這個物件。|  
  
### 公用常數  
  
|名稱|描述|  
|--------|--------|  
|[tiled\_extent::tile\_dim0 常數](../Topic/tiled_extent::tile_dim0%20Constant.md)|儲存最高有效維度的長度。|  
|[tiled\_extent::tile\_dim1 常數](../Topic/tiled_extent::tile_dim1%20Constant.md)|儲存次高有效維度的長度。|  
|[tiled\_extent::tile\_dim2 常數](../Topic/tiled_extent::tile_dim2%20Constant.md)|儲存最低有效維度的長度。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[tiled\_extent::tile\_extent 資料成員](../Topic/tiled_extent::tile_extent%20Data%20Member.md)|取得 `extent` 物件，這個物件會擷取 `tiled_extent` 樣板引數 `_Dim0`、`_Dim1` 和 `_Dim2` 的值。|  
  
## 繼承階層架構  
 `extent`  
  
 `tiled_extent`  
  
## 需求  
 **標頭：**amp.h  
  
 **命名空間：**並行  
  
## 請參閱  
 [Concurrency 命名空間 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)