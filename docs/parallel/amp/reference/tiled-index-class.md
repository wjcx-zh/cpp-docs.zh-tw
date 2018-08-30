---
title: tiled_index 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- tiled_index
- AMP/tiled_index
- AMP/Concurrency::tiled_index::tiled_index
- AMP/Concurrency::tiled_index::get_tile_extent
- AMP/Concurrency::tiled_index::barrier
- AMP/Concurrency::tiled_index::global
- AMP/Concurrency::tiled_index::local
- AMP/Concurrency::tiled_index::rank
- AMP/Concurrency::tiled_index::tile
- AMP/Concurrency::tiled_index::tile_dim0
- AMP/Concurrency::tiled_index::tile_dim1
- AMP/Concurrency::tiled_index::tile_dim2
- AMP/Concurrency::tiled_index::tile_origin
- AMP/Concurrency::tiled_index::tile_extent
dev_langs:
- C++
helpviewer_keywords:
- tiled_index class
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ed19dd2a1b62a3682d96f8c9a596fa6a4b1b377
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209429"
---
# <a name="tiledindex-class"></a>tiled_index 類別
提供的索引[tiled_extent](tiled-extent-class.md)物件。 這個類別具有存取相對於本機磚原點和相對於全域原點的項目屬性。 如需劃分 tile 空間的詳細資訊，請參閱[使用的圖格](../../../parallel/amp/using-tiles.md)。  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 `_Dim0`  
 最高有效維度的長度。  
  
 `_Dim1`  
 下一步 以最高有效維度的長度。  
  
 `_Dim2`  
 最小顯著性維度的長度。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[tiled_index 建構函式](#ctor)|初始化 `tile_index` 類別的新執行個體。|  

  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[get_tile_extent](#tiled_index__get_tile_extent)|傳回[程度](extent-class.md)的值的物件`tiled_index`樣板引數`_Dim0`， `_Dim1`，和`_Dim2`。|  


  
### <a name="public-constants"></a>公用常數  
  
|名稱|描述|  
|----------|-----------------|  
|[barrier 常數](#tiled_index__barrier)|存放區[tile_barrier](tile-barrier-class.md)物件，表示執行緒之目前磚中的屏障。|  
|||  
|[全域常數](#tiled_index__global)|存放區[index](index-class.md)物件中的陣序規範 1、 2 或 3，表示全域索引[格線](https://msdn.microsoft.com/f7d1b6a6-586c-4345-b09a-bfc26c492cb0)物件。|  
|[區域常數](#tiled_index__local)|存放區`index`物件的陣序規範 1、 2 或 3，表示相對於索引中之目前磚[tiled_extent](tiled-extent-class.md)物件。|  
|[rank 常數](#tiled_index__rank)|儲存的陣序`tiled_index`物件。|  
|[tile 常數](#tiled_index__tile)|存放區`index`物件的陣序規範 1、 2 或 3，表示目前的圖格的座標`tiled_extent`物件。|  
|[tile_dim0 常數](#tiled_index__tile_dim0)|儲存的最高有效維度的長度。|  
|[tile_dim1 常數](#tiled_index__tile_dim1)|儲存下一步 以最高有效維度的長度。|  
|[tile_dim2 常數](#tiled_index__tile_dim2)|儲存最低有效維度的長度。|  
|[tile_origin 常數](#tiled_index__tile_origin)|存放區`index`物件中目前磚原點的陣序規範 1、 2 或 3，表示全域座標`tiled_extent`物件。|  

  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[tile_extent](#tile_extent)|取得[程度](extent-class.md)的值的物件`tiled_index`樣板引數`tiled_index`樣板引數`_Dim0`， `_Dim1`，和`_Dim2`。|  

  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `_Tiled_index_base`  
  
 `tiled_index`  
  
## <a name="requirements"></a>需求  
 **標頭︰** amp.h  
  
 **命名空間：** 並行  


## <a name="tiled_index__ctor"></a>  tiled_index 建構函式  
初始化 `tiled_index` 類別的新執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
tiled_index(  
    const index<rank>& _Global,  
    const index<rank>& _Local,  
    const index<rank>& _Tile,  
    const index<rank>& _Tile_origin,  
    const tile_barrier& _Barrier ) restrict(amp,cpu);  
  
tiled_index(  
    const tiled_index& _Other ) restrict(amp,cpu);  
```  
  
#### <a name="parameters"></a>參數  
 `_Global`  
 全域[index](index-class.md)建構`tiled_index`。  
  
 `_Local`  
 本機[index](index-class.md)建構 `tiled_index`  
  
 `_Tile`  
 [] 圖格[index](index-class.md)建構 `tiled_index`  
  
 `_Tile_origin`  
 並排原點[index](index-class.md)建構 `tiled_index`  
  
 `_Barrier`  
 [Tile_barrier](tile-barrier-class.md)物件的建構`tiled_index`。  
  
 `_Other`  
 `tile_index`要複製的物件以建構`tiled_index`。  
  
## <a name="overloads"></a>Overloads  
  
|||  
|-|-|  
|名稱|描述|  
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|初始化的新執行個體`tile_index`並排在全域座標和並排在區域座標的相對位置從索引類別。 `_Global`和`_Tile_origin`參數會經過計算。|  
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|初始化的新執行個體`tile_index`藉由複製指定的類別`tiled_index`物件。|  


## <a name="tiled_index__get_tile_extent"></a>  get_tile_extent
傳回[程度](extent-class.md)的值的物件`tiled_index`樣板引數`_Dim0`， `_Dim1`，和`_Dim2`。  
  
## <a name="syntax"></a>語法  
  
```  
extent<rank> get_tile_extent()restrict(amp,cpu);  
```  
  
## <a name="return-value"></a>傳回值  
 `extent`的值的物件`tiled_index`樣板引數`_Dim0`， `_Dim1`，和`_Dim2`。  

## <a name="tiled_index__barrier"></a>  barrier   
存放區[tile_barrier](tile-barrier-class.md)物件，表示執行緒之目前磚中的屏障。  
  
## <a name="syntax"></a>語法  
  
```  
const tile_barrier barrier;  
```  

## <a name="tiled_index__global"></a>  全域   
存放區[index](index-class.md)物件的陣序規範 1、 2 或 3，表示物件的全域索引。  
  
## <a name="syntax"></a>語法  
  
```  
const index<rank> global;  
```  
  
## <a name="tiled_index__local"></a>  本機   
存放區[index](index-class.md)物件的陣序規範 1、 2 或 3，表示相對於索引中之目前磚[tiled_extent](tiled-extent-class.md)物件。  
  
## <a name="syntax"></a>語法  
  
```  
const index<rank> local;  
```  
  
## <a name="tiled_index__rank"></a>  陣序規範   
儲存的陣序`tiled_index`物件。  
  
## <a name="syntax"></a>語法  
  
```  
static const int rank = _Rank;  
```  

## <a name="tiled_index__tile"></a>  圖格   
存放區[index](index-class.md)物件的陣序規範 1、 2 或 3，表示目前的圖格的座標[tiled_extent](tiled-extent-class.md)物件。  
  
## <a name="syntax"></a>語法  
  
```  
const index<rank> tile;  
```  
  
## <a name="tiled_index__tile_dim0"></a>  tile_dim0  
儲存的最高有效維度的長度。  
  
## <a name="syntax"></a>語法  
  
```  
static const int tile_dim0 = _Dim0;  
```  
   
## <a name="tiled_index__tile_dim1"></a>  tile_dim1   
儲存下一步 以最高有效維度的長度。  
  
## <a name="syntax"></a>語法  
  
```  
static const int tile_dim1 = _Dim1;  
```  
## <a name="tiled_index__tile_dim2"></a>  tile_dim2   
儲存最低有效維度的長度。  
  
## <a name="syntax"></a>語法  
  
```  
static const int tile_dim2 = _Dim2;  
```  
## <a name="tiled_index__tile_origin"></a>  tile_origin   
存放區[index](index-class.md)物件的陣序規範 1、 2 或 3，表示全域座標之原點的內目前的圖格[tiled_extent](tiled-extent-class.md)物件。  
  
## <a name="syntax"></a>語法  
  
```  
const index<rank> tile_origin  
```  
## <a name="tile_extent"></a>  tile_extent
  取得[程度](extent-class.md)的值的物件`tiled_index`樣板引數`tiled_index`樣板引數`_Dim0`， `_Dim1`，和`_Dim2`。  
  
## <a name="syntax"></a>語法  
  
```  
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;  
```  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
