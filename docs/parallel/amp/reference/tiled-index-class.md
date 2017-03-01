---
title: "tiled_index 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::tiled_index
dev_langs:
- C++
helpviewer_keywords:
- tiled_index class
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 2c10721f40bd1c90a196ba82655482f35a8e10d8
ms.lasthandoff: 02/24/2017

---
# <a name="tiledindex-class"></a>tiled_index 類別
提供的索引[tiled_extent](tiled-extent-class.md)物件。 此類別具有存取項目相對於本機磚原點和相對於全域原點的屬性。 如需並排顯示空間的詳細資訊，請參閱[使用磚](../../../parallel/amp/using-tiles.md)。  
  
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
 最重要的維度的長度。  
  
 `_Dim1`  
 下一步 以最重要維度的長度。  
  
 `_Dim2`  
 最小顯著性的維度的長度。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[tiled_index 建構函式](#ctor)|初始化 `tile_index` 類別的新執行個體。|  

  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[get_tile_extent 方法](#tiled_index__get_tile_extent)|傳回[範圍](extent-class.md)物件的值，`tiled_index`樣板引數`_Dim0`， `_Dim1`，和`_Dim2`。|  


  
### <a name="public-constants"></a>公用常數  
  
|名稱|說明|  
|----------|-----------------|  
|[barrier 常數](#tiled_index__barrier)|存放區[tile_barrier](tile-barrier-class.md)物件，表示目前執行緒磚中的屏障。|  
|||  
|[全域常數](#tiled_index__global)|存放區[索引](index-class.md)物件中的陣序規範 1、 2 或 3 代表全域索引[方格](http://msdn.microsoft.com/en-us/f7d1b6a6-586c-4345-b09a-bfc26c492cb0)物件。|  
|[local 常數](#tiled_index__local)|存放區`index`物件的目前 tile 中的陣序規範 1、 2 或 3，表示相對於索引[tiled_extent](tiled-extent-class.md)物件。|  
|[rank 常數](#tiled_index__rank)|儲存的陣序規範`tiled_index`物件。|  
|[tile 常數](#tiled_index__tile)|存放區`index`陣序規範 1、 2 或 3，代表目前的圖格的座標的物件`tiled_extent`物件。|  
|[tile_dim0 常數](#tiled_index__tile_dim0)|儲存最大顯著性的維度的長度。|  
|[tile_dim1 常數](#tiled_index__tile_dim1)|儲存下一步 以最重要維度的長度。|  
|[tile_dim2 常數](#tiled_index__tile_dim2)|儲存最小顯著性的維度的長度。|  
|[tile_origin 常數](#tiled_index__tile_origin)|存放區`index`物件的目前 tile 中的原始來源的陣序規範 1、 2 或 3 代表全域座標`tiled_extent`物件。|  

  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[tile_extent 資料成員](#tile_extent)|取得[範圍](extent-class.md)物件的值，`tiled_index`樣板引數`tiled_index`樣板引數`_Dim0`， `_Dim1`，和`_Dim2`。|  

  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `_Tiled_index_base`  
  
 `tiled_index`  
  
## <a name="requirements"></a>需求  
 **標頭︰** amp.h  
  
 **命名空間：** 並行  


## <a name="a-nametiledindexctora--tiledindex-constructor"></a><a name="tiled_index__ctor"></a>tiled_index 建構函式  
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
 全域[索引](index-class.md)建構`tiled_index`。  
  
 `_Local`  
 本機[索引](index-class.md)建構`tiled_index`  
  
 `_Tile`  
 磚[索引](index-class.md)建構`tiled_index`  
  
 `_Tile_origin`  
 並排顯示原始[索引](index-class.md)建構`tiled_index`  
  
 `_Barrier`  
 [Tile_barrier](tile-barrier-class.md)物件建構`tiled_index`。  
  
 `_Other`  
 `tile_index`要複製的物件來建構`tiled_index`。  
  
## <a name="overloads"></a>Overloads  
  
|||  
|-|-|  
|名稱|說明|  
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|初始化的新執行個體`tile_index`類別從索引中全域座標磚和座標中的方塊中的相對位置。 `_Global`和`_Tile_origin`參數來計算。|  
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|初始化的新執行個體`tile_index`複製指定的類別`tiled_index`物件。|  


## <a name="a-nametiledindexgettileextenta--gettileextent"></a><a name="tiled_index__get_tile_extent"></a>get_tile_extent
傳回[範圍](extent-class.md)物件的值，`tiled_index`樣板引數`_Dim0`， `_Dim1`，和`_Dim2`。  
  
## <a name="syntax"></a>語法  
  
```  
extent<rank> get_tile_extent()restrict(amp,cpu);  
```  
  
## <a name="return-value"></a>傳回值  
 `extent`物件的值，`tiled_index`樣板引數`_Dim0`， `_Dim1`，和`_Dim2`。  

## <a name="a-nametiledindexbarriera--barrier"></a><a name="tiled_index__barrier"></a>屏障   
存放區[tile_barrier](tile-barrier-class.md)物件，表示目前執行緒磚中的屏障。  
  
## <a name="syntax"></a>語法  
  
```  
const tile_barrier barrier;  
```  

## <a name="a-nametiledindexglobala--global"></a><a name="tiled_index__global"></a>全域   
存放區[索引](index-class.md)的陣序規範 1、 2 或 3，表示全域物件的索引物件。  
  
## <a name="syntax"></a>語法  
  
```  
const index<rank> global;  
```  
  
## <a name="a-nametiledindexlocala--local"></a><a name="tiled_index__local"></a>本機   
存放區[索引](index-class.md)物件的目前 tile 中的陣序規範 1、 2 或 3，表示相對於索引[tiled_extent](tiled-extent-class.md)物件。  
  
## <a name="syntax"></a>語法  
  
```  
const index<rank> local;  
```  
  
## <a name="a-nametiledindexranka--rank"></a><a name="tiled_index__rank"></a>陣序規範   
儲存的陣序規範`tiled_index`物件。  
  
## <a name="syntax"></a>語法  
  
```  
static const int rank = _Rank;  
```  

## <a name="a-nametiledindextilea--tile"></a><a name="tiled_index__tile"></a>並排顯示   
存放區[索引](index-class.md)陣序規範 1、 2 或 3，代表目前的圖格的座標的物件[tiled_extent](tiled-extent-class.md)物件。  
  
## <a name="syntax"></a>語法  
  
```  
const index<rank> tile;  
```  
  
## <a name="a-nametiledindextiledim0a--tiledim0"></a><a name="tiled_index__tile_dim0"></a>tile_dim0  
儲存最大顯著性的維度的長度。  
  
## <a name="syntax"></a>語法  
  
```  
static const int tile_dim0 = _Dim0;  
```  
   
## <a name="a-nametiledindextiledim1a--tiledim1"></a><a name="tiled_index__tile_dim1"></a>tile_dim1   
儲存下一步 以最重要維度的長度。  
  
## <a name="syntax"></a>語法  
  
```  
static const int tile_dim1 = _Dim1;  
```  
## <a name="a-nametiledindextiledim2a--tiledim2"></a><a name="tiled_index__tile_dim2"></a>tile_dim2   
儲存最小顯著性的維度的長度。  
  
## <a name="syntax"></a>語法  
  
```  
static const int tile_dim2 = _Dim2;  
```  
## <a name="a-nametiledindextileorigina--tileorigin"></a><a name="tiled_index__tile_origin"></a>tile_origin   
存放區[索引](index-class.md)物件的目前 tile 中的原始來源的陣序規範 1、 2 或 3 代表全域座標[tiled_extent](tiled-extent-class.md)物件。  
  
## <a name="syntax"></a>語法  
  
```  
const index<rank> tile_origin  
```  
## <a name="a-nametileextenta--tileextent"></a><a name="tile_extent"></a>tile_extent
  取得[範圍](extent-class.md)物件的值，`tiled_index`樣板引數`tiled_index`樣板引數`_Dim0`， `_Dim1`，和`_Dim2`。  
  
## <a name="syntax"></a>語法  
  
```  
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;  
```  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (c + + AMP)](concurrency-namespace-cpp-amp.md)

