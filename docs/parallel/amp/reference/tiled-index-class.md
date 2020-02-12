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
ms.openlocfilehash: eda01667a6b239284c682ba6ae3f9b857c713447
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142428"
---
# <a name="tiled_index-class"></a>tiled_index 類別

提供[tiled_extent](tiled-extent-class.md)物件的索引。 這個類別具有屬性，可存取相對於本機磚來源的專案，以及相對於全域來源的元素。 如需磚空間的詳細資訊，請參閱[使用磚](../../../parallel/amp/using-tiles.md)。

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
下一個最重要維度的長度。

*_Dim2*<br/>
最不重要維度的長度。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[tiled_index 的構造函式](#ctor)|初始化 `tile_index` 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[get_tile_extent](#tiled_index__get_tile_extent)|傳回具有 `tiled_index` 樣板引數值 `_Dim0`、`_Dim1`和 `_Dim2`的[範圍](extent-class.md)物件。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[屏障常數](#tiled_index__barrier)|儲存代表目前線程磚中之屏障的[tile_barrier](tile-barrier-class.md)物件。|
|||
|[全域常數](#tiled_index__global)|儲存次序1、2或3的[索引](index-class.md)物件，代表方格物件中的全域索引。|
|[本機常數](#tiled_index__local)|儲存次序1、2或3的 `index` 物件，代表[tiled_extent](tiled-extent-class.md)物件目前磚中的相對索引。|
|[次序常數](#tiled_index__rank)|儲存 `tiled_index` 物件的順位。|
|[磚常數](#tiled_index__tile)|儲存次序1、2或3的 `index` 物件，代表 `tiled_extent` 物件之目前磚的座標。|
|[tile_dim0 常數](#tiled_index__tile_dim0)|儲存最重要維度的長度。|
|[tile_dim1 常數](#tiled_index__tile_dim1)|儲存下一個最重要維度的長度。|
|[tile_dim2 常數](#tiled_index__tile_dim2)|儲存最不重要維度的長度。|
|[tile_origin 常數](#tiled_index__tile_origin)|儲存次序1、2或3的 `index` 物件，代表 `tiled_extent` 物件中目前磚原點的全域座標。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[tile_extent](#tile_extent)|取得具有 `tiled_index` 樣板引數值的[範圍](extent-class.md)物件，`tiled_index` 樣板引數 `_Dim0`、`_Dim1`和 `_Dim2`。|

## <a name="inheritance-hierarchy"></a>繼承階層

`_Tiled_index_base`

`tiled_index`

## <a name="requirements"></a>需求

**標頭︰** amp.h

**命名空間：** 並行

## <a name="ctor"></a>tiled_index 的構造函式

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
結構化 `tiled_index`的全域[索引](index-class.md)。

*_Local*<br/>
結構化 `tiled_index` 的本機[索引](index-class.md)

*_Tile*<br/>
結構化 `tiled_index` 的磚[索引](index-class.md)

*_Tile_origin*<br/>
結構化 `tiled_index` 的磚來源[索引](index-class.md)

*_Barrier*<br/>
已結構化 `tiled_index`的[tile_barrier](tile-barrier-class.md)物件。

*_Other*<br/>
要複製到所結構 `tiled_index`的 `tile_index` 物件。

### <a name="overloads"></a>Overloads

|||
|-|-|
|名稱|描述|
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|從全域座標的磚索引和磚中的相對位置（區域座標），初始化 `tile_index` 類別的新實例。 系統會計算 `_Global` 和 `_Tile_origin` 參數。|
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|藉由複製指定的 `tiled_index` 物件，初始化 `tile_index` 類別的新實例。|

## <a name="tiled_index__get_tile_extent"></a>get_tile_extent

傳回具有 `tiled_index` 樣板引數值 `_Dim0`、`_Dim1`和 `_Dim2`的[範圍](extent-class.md)物件。

### <a name="syntax"></a>語法

```cpp
extent<rank> get_tile_extent()restrict(amp,cpu);
```

### <a name="return-value"></a>傳回值

`extent` 物件，其中包含 `tiled_index` 樣板引數的值 `_Dim0`、`_Dim1`和 `_Dim2`。

## <a name="tiled_index__barrier"></a>屏障

儲存代表目前線程磚中之屏障的[tile_barrier](tile-barrier-class.md)物件。

### <a name="syntax"></a>語法

```cpp
const tile_barrier barrier;
```

## <a name="tiled_index__global"></a>全域性

儲存次序1、2或3的[索引](index-class.md)物件，代表物件的全域索引。

### <a name="syntax"></a>語法

```cpp
const index<rank> global;
```

## <a name="tiled_index__local"></a>本機

儲存次序1、2或3的[索引](index-class.md)物件，代表[tiled_extent](tiled-extent-class.md)物件的目前磚中的相對索引。

### <a name="syntax"></a>語法

```cpp
const index<rank> local;
```

## <a name="tiled_index__rank"></a>等級

儲存 `tiled_index` 物件的順位。

### <a name="syntax"></a>語法

```cpp
static const int rank = _Rank;
```

## <a name="tiled_index__tile"></a>圖示

儲存次序1、2或3的[索引](index-class.md)物件，表示[tiled_extent](tiled-extent-class.md)物件之目前磚的座標。

### <a name="syntax"></a>語法

```cpp
const index<rank> tile;
```

## <a name="tiled_index__tile_dim0"></a>tile_dim0

儲存最重要維度的長度。

### <a name="syntax"></a>語法

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tiled_index__tile_dim1"></a>tile_dim1

儲存下一個最重要維度的長度。

### <a name="syntax"></a>語法

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tiled_index__tile_dim2"></a>tile_dim2

儲存最不重要維度的長度。

### <a name="syntax"></a>語法

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tiled_index__tile_origin"></a>tile_origin

儲存次序1、2或3的[索引](index-class.md)物件，代表[tiled_extent](tiled-extent-class.md)物件內目前磚的原點的全域座標。

### <a name="syntax"></a>語法

```cpp
const index<rank> tile_origin
```

## <a name="tile_extent"></a>tile_extent

取得具有 `tiled_index` 樣板引數值的[範圍](extent-class.md)物件，`tiled_index` 樣板引數 `_Dim0`、`_Dim1`和 `_Dim2`。

### <a name="syntax"></a>語法

```cpp
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;
```

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
