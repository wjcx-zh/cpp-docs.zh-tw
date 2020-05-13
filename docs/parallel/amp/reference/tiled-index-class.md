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
ms.openlocfilehash: 46a6b3548526f0917c4e022a12bf859242e70b20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375474"
---
# <a name="tiled_index-class"></a>tiled_index 類別

提供索引到[tiled_extent](tiled-extent-class.md)物件。 此類具有訪問相對於局部磁貼源和全域源的元素的屬性。 有關平鋪空間的詳細資訊,請參閱[使用磁貼](../../../parallel/amp/using-tiles.md)。

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
最重要的維度的長度。

*_Dim1*<br/>
第二個最重要的維度的長度。

*_Dim2*<br/>
最小尺寸的長度。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[tiled_index構構函數](#ctor)|將 `tile_index` 類別的新執行個體初始化。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[get_tile_extent](#tiled_index__get_tile_extent)|傳回`tiled_index`樣式`_Dim0``_Dim1`,[extent](extent-class.md)與`_Dim2`。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[屏障常數](#tiled_index__barrier)|存儲表示當前線程磁貼中障礙[tile_barrier](tile-barrier-class.md)物件。|
|||
|[全域常數](#tiled_index__global)|存儲表示網格物件中全域索引的排名為 1、2 或 3 的[索引](index-class.md)物件。|
|[local 常數](#tiled_index__local)|存儲排名`index`1、2 或 3 的物件,該物件表示[tiled_extent](tiled-extent-class.md)物件的當前磁貼中的相對索引。|
|[排名 常量](#tiled_index__rank)|存儲`tiled_index`物件的排名。|
|[磁貼常數](#tiled_index__tile)|存儲表示`index``tiled_extent`物件當前磁貼座標的排名為 1、2 或 3 的物件。|
|[tile_dim0常量](#tiled_index__tile_dim0)|存儲最重要的維度的長度。|
|[tile_dim1常量](#tiled_index__tile_dim1)|存儲第二個最重要的維度的長度。|
|[tile_dim2常量](#tiled_index__tile_dim2)|存儲最小尺寸的長度。|
|[tile_origin常量](#tiled_index__tile_origin)|存儲排名`index`1、2 或 3 的物件`tiled_extent`,該物件表示 物件中當前磁貼的原點的全域座標。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[tile_extent](#tile_extent)|取得樣`tiled_index`式`tiled_index`的範本參數樣本`_Dim0`參數的數值的[延伸區](extent-class.md)`_Dim1`物件`_Dim2`, 與 。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`_Tiled_index_base`

`tiled_index`

## <a name="requirements"></a>需求

**標頭︰** amp.h

**命名空間：** 並行

## <a name="tiled_index-constructor"></a><a name="ctor"></a>tiled_index構構函數

將 `tiled_index` 類別的新執行個體初始化。

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
建構`tiled_index`的全域[索引](index-class.md)。

*_Local*<br/>
建構的局部[索引](index-class.md)`tiled_index`

*_Tile*<br/>
建構的磁貼[索引](index-class.md)`tiled_index`

*_Tile_origin*<br/>
建構的切片原點[索引](index-class.md)`tiled_index`

*_Barrier*<br/>
建構的[tile_barrier](tile-barrier-class.md)tile_barrier`tiled_index`物件 。

*_Other*<br/>
要`tile_index`複製到構造`tiled_index`的物件。

### <a name="overloads"></a>Overloads

|||
|-|-|
|名稱|描述|
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|從全域座標中的磁貼索引和局部`tile_index`座標中磁貼的相對位置初始化類的新實例。 計算`_Global``_Tile_origin`和 參數。|
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|通過複製指定的`tile_index``tiled_index`物件來初始化類的新實例。|

## <a name="get_tile_extent"></a><a name="tiled_index__get_tile_extent"></a>get_tile_extent

傳回`tiled_index`樣式`_Dim0``_Dim1`,[extent](extent-class.md)與`_Dim2`。

### <a name="syntax"></a>語法

```cpp
extent<rank> get_tile_extent()restrict(amp,cpu);
```

### <a name="return-value"></a>傳回值

具有`extent``tiled_index`樣本參數`_Dim0`的值的物件`_Dim1`,`_Dim2`和 .

## <a name="barrier"></a><a name="tiled_index__barrier"></a>障礙

存儲表示當前線程磁貼中障礙[tile_barrier](tile-barrier-class.md)物件。

### <a name="syntax"></a>語法

```cpp
const tile_barrier barrier;
```

## <a name="global"></a><a name="tiled_index__global"></a>全球

存儲表示物件的全域索引的排名 1、2 或 3 的[索引](index-class.md)物件。

### <a name="syntax"></a>語法

```cpp
const index<rank> global;
```

## <a name="local"></a><a name="tiled_index__local"></a>當地

存儲排名 1、2 或 3 的[索引](index-class.md)物件,該物件表示[tiled_extent](tiled-extent-class.md)物件的當前磁貼中的相對索引。

### <a name="syntax"></a>語法

```cpp
const index<rank> local;
```

## <a name="rank"></a><a name="tiled_index__rank"></a>排名

存儲`tiled_index`物件的排名。

### <a name="syntax"></a>語法

```cpp
static const int rank = _Rank;
```

## <a name="tile"></a><a name="tiled_index__tile"></a>瓦

存儲表示[tiled_extent](tiled-extent-class.md)物件的當前磁貼的座標的排名 1、2 或 3 的[索引](index-class.md)物件。

### <a name="syntax"></a>語法

```cpp
const index<rank> tile;
```

## <a name="tile_dim0"></a><a name="tiled_index__tile_dim0"></a>tile_dim0

存儲最重要的維度的長度。

### <a name="syntax"></a>語法

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tiled_index__tile_dim1"></a>tile_dim1

存儲第二個最重要的維度的長度。

### <a name="syntax"></a>語法

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tiled_index__tile_dim2"></a>tile_dim2

存儲最小尺寸的長度。

### <a name="syntax"></a>語法

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_origin"></a><a name="tiled_index__tile_origin"></a>tile_origin

存儲排名 1、2 或 3 的索引物件,該[索引](index-class.md)物件表示[tiled_extent](tiled-extent-class.md)物件中當前磁貼的原點的全域座標。

### <a name="syntax"></a>語法

```cpp
const index<rank> tile_origin
```

## <a name="tile_extent"></a><a name="tile_extent"></a>tile_extent

取得樣`tiled_index`式`tiled_index`的範本參數樣本`_Dim0`參數的數值的[延伸區](extent-class.md)`_Dim1`物件`_Dim2`, 與 。

### <a name="syntax"></a>語法

```cpp
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;
```

## <a name="see-also"></a>另請參閱

[併發命名空間(C++ AMP)](concurrency-namespace-cpp-amp.md)
