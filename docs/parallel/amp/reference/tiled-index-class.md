---
title: tiled_index 類別
ms.date: 03/27/2019
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
helpviewer_keywords:
- tiled_index class
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
ms.openlocfilehash: 9d295093031eaee0a2d4dd83aa931060e6eebc07
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832266"
---
# <a name="tiled_index-class"></a>tiled_index 類別

在 [tiled_extent](tiled-extent-class.md) 物件中提供索引。 此類別具有屬性，可存取相對於本機磚原點的專案，以及相對於全域來源的專案。 如需磚空間的詳細資訊，請參閱 [使用磚](../../../parallel/amp/using-tiles.md)。

## <a name="syntax"></a>語法

```cpp
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

### <a name="parameters"></a>參數

*_Dim0*<br/>
最重要維度的長度。

*_Dim1*<br/>
下個最重要維度的長度。

*_Dim2*<br/>
最不重要維度的長度。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[tiled_index 的函式](#ctor)|初始化 `tile_index` 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[get_tile_extent](#tiled_index__get_tile_extent)|傳回具有[extent](extent-class.md) `tiled_index` 範本引數 `_Dim0` 、和的值的範圍物件 `_Dim1` `_Dim2` 。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[屏障常數](#tiled_index__barrier)|儲存 [tile_barrier](tile-barrier-class.md) 物件，代表目前線程磚中的關卡。|
|[全域常數](#tiled_index__global)|儲存等級1、2或3的 [索引](index-class.md) 物件，代表方格物件中的全域索引。|
|[local 常數](#tiled_index__local)|儲存 `index` 等級1、2或3的物件，代表 [tiled_extent](tiled-extent-class.md) 物件目前磚中的相對索引。|
|[排名常數](#tiled_index__rank)|儲存物件的順位 `tiled_index` 。|
|[磚常數](#tiled_index__tile)|儲存 `index` 等級1、2或3的物件，代表物件目前磚的座標 `tiled_extent` 。|
|[tile_dim0 常數](#tiled_index__tile_dim0)|儲存最重要維度的長度。|
|[tile_dim1 常數](#tiled_index__tile_dim1)|儲存下個最重要維度的長度。|
|[tile_dim2 常數](#tiled_index__tile_dim2)|儲存最不重要維度的長度。|
|[tile_origin 常數](#tiled_index__tile_origin)|儲存 `index` 等級1、2或3的物件，代表物件中目前磚原點的全域座標 `tiled_extent` 。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[tile_extent](#tile_extent)|取得具有[extent](extent-class.md) `tiled_index` 範本引數樣板 `tiled_index` 引數 `_Dim0` 、 `_Dim1` 和值的範圍物件 `_Dim2` 。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`_Tiled_index_base`

`tiled_index`

## <a name="requirements"></a>規格需求

**標頭︰** amp.h

**命名空間：** 並行

## <a name="tiled_index-constructor"></a><a name="ctor"></a> tiled_index 的函式

初始化 `tiled_index` 類別的新執行個體。

### <a name="syntax"></a>語法

```cpp
tiled_index(
    const index<rank>& _Global,
    const index<rank>& _Local,
    const index<rank>& _Tile,
    const index<rank>& _Tile_origin,
    const tile_barrier& _Barrier ) restrict(amp,cpu);

tiled_index(
    const tiled_index& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Global*<br/>
所結構[index](index-class.md)化的全域索引 `tiled_index` 。

*_Local*<br/>
所建立之的本機[索引](index-class.md)`tiled_index`

*_Tile*<br/>
所建立之的圖格[索引](index-class.md)`tiled_index`

*_Tile_origin*<br/>
所建立之的磚原始[索引](index-class.md)`tiled_index`

*_Barrier*<br/>
所建立之的 [tile_barrier](tile-barrier-class.md) 物件 `tiled_index` 。

*_Other*<br/>
`tile_index`要複製到所結構化的物件 `tiled_index` 。

### <a name="overloads"></a>多載

|名稱|描述|
|-|-|
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|`tile_index`從全域座標中磚的索引，以及磚中的區域座標，初始化類別的新實例。 `_Global` `_Tile_origin` 會計算和參數。|
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|藉由複製指定的物件，初始化類別的新實例 `tile_index` `tiled_index` 。|

## <a name="get_tile_extent"></a><a name="tiled_index__get_tile_extent"></a> get_tile_extent

傳回具有[extent](extent-class.md) `tiled_index` 範本引數 `_Dim0` 、和的值的範圍物件 `_Dim1` `_Dim2` 。

### <a name="syntax"></a>語法

```cpp
extent<rank> get_tile_extent()restrict(amp,cpu);
```

### <a name="return-value"></a>傳回值

`extent`具有 `tiled_index` 範本引數 `_Dim0` 、和的值的物件 `_Dim1` `_Dim2` 。

## <a name="barrier"></a><a name="tiled_index__barrier"></a> 障礙

儲存 [tile_barrier](tile-barrier-class.md) 物件，代表目前線程磚中的關卡。

### <a name="syntax"></a>語法

```cpp
const tile_barrier barrier;
```

## <a name="global"></a><a name="tiled_index__global"></a> 全球

儲存等級1、2或3的 [索引](index-class.md) 物件，代表物件的全域索引。

### <a name="syntax"></a>語法

```cpp
const index<rank> global;
```

## <a name="local"></a><a name="tiled_index__local"></a> 當地

儲存等級1、2或3的 [索引](index-class.md) 物件，代表 [tiled_extent](tiled-extent-class.md) 物件目前磚中的相對索引。

### <a name="syntax"></a>語法

```cpp
const index<rank> local;
```

## <a name="rank"></a><a name="tiled_index__rank"></a> 排名

儲存物件的順位 `tiled_index` 。

### <a name="syntax"></a>語法

```cpp
static const int rank = _Rank;
```

## <a name="tile"></a><a name="tiled_index__tile"></a> 瓦

儲存等級1、2或3的 [索引](index-class.md) 物件，表示 [tiled_extent](tiled-extent-class.md) 物件目前磚的座標。

### <a name="syntax"></a>語法

```cpp
const index<rank> tile;
```

## <a name="tile_dim0"></a><a name="tiled_index__tile_dim0"></a> tile_dim0

儲存最重要維度的長度。

### <a name="syntax"></a>語法

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tiled_index__tile_dim1"></a> tile_dim1

儲存下個最重要維度的長度。

### <a name="syntax"></a>語法

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tiled_index__tile_dim2"></a> tile_dim2

儲存最不重要維度的長度。

### <a name="syntax"></a>語法

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_origin"></a><a name="tiled_index__tile_origin"></a> tile_origin

儲存等級1、2或3的 [索引](index-class.md) 物件，代表 [tiled_extent](tiled-extent-class.md) 物件內目前磚之原點的全域座標。

### <a name="syntax"></a>語法

```cpp
const index<rank> tile_origin
```

## <a name="tile_extent"></a><a name="tile_extent"></a> tile_extent

取得具有[extent](extent-class.md) `tiled_index` 範本引數樣板 `tiled_index` 引數 `_Dim0` 、 `_Dim1` 和值的範圍物件 `_Dim2` 。

### <a name="syntax"></a>語法

```cpp
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;
```

## <a name="see-also"></a>另請參閱

[並行命名空間 (C++ AMP) ](concurrency-namespace-cpp-amp.md)
