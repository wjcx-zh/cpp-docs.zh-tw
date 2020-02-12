---
title: tiled_extent 類別
ms.date: 11/04/2016
f1_keywords:
- tiled_extent
- AMP/tiled_extent
- AMP/Concurrency::tiled_extent::tiled_extent
- AMP/Concurrency::tiled_extent::get_tile_extent
- AMP/Concurrency::tiled_extent::pad
- AMP/Concurrency::tiled_extent::truncate
- AMP/Concurrency::tiled_extent::tile_dim0
- AMP/Concurrency::tiled_extent::tile_dim1
- AMP/Concurrency::tiled_extent::tile_dim2
- AMP/Concurrency::tiled_extent::tile_extent
ms.assetid: 671ecaf8-c7b0-4ac8-bbdc-e30bd92da7c0
ms.openlocfilehash: e2248c770c7eedde59d1cb592f7d5d7c1bfbde9a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126418"
---
# <a name="tiled_extent-class"></a>tiled_extent 類別

`tiled_extent` 物件是一到三個維度的 `extent` 物件，可將範圍空間會細分成一、兩個或三維的磚。

## <a name="syntax"></a>語法

```cpp
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
|[tiled_extent 的構造函式](#ctor)|初始化 `tiled_extent` 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[get_tile_extent](#get_tile_extent)|傳回 `extent` 物件，它會捕獲 `tiled_extent` 樣板引數的值 `_Dim0`、`_Dim1`和 `_Dim2`。|
|[pad](#pad)|傳回新的 `tiled_extent` 物件，其中的範圍已調整為要由磚維度平均地整除。|
|[truncate](#truncate)|傳回新的 `tiled_extent` 物件，並將範圍向下調整，以供磚維度平均地整除。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator=](#operator_eq)|將指定 `tiled_index` 物件的內容複寫到這個。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[tile_dim0 常數](#tile_dim0)|儲存最重要維度的長度。|
|[tile_dim1 常數](#tile_dim1)|儲存下一個最重要維度的長度。|
|[tile_dim2 常數](#tile_dim2)|儲存最不重要維度的長度。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[tile_extent](#tile_extent)|取得 `extent` 物件，其會捕獲 `tiled_extent` 樣板引數的值 `_Dim0`、`_Dim1`和 `_Dim2`。|

## <a name="inheritance-hierarchy"></a>繼承階層

`extent`

`tiled_extent`

## <a name="requirements"></a>需求

**標頭︰** amp.h

**命名空間：** 並行

## <a name="ctor"></a> Tiled_extent 的構造函式

初始化 `tiled_extent` 類別的新執行個體。

### <a name="syntax"></a>語法

```cpp
tiled_extent();

tiled_extent(
    const Concurrency::extent<rank>& _Other );

tiled_extent(
    const tiled_extent& _Other );
```

### <a name="parameters"></a>參數

*_Other*<br/>
要複製的 `extent` 或 `tiled_extent` 物件。

## <a name="get_tile_extent"></a> get_tile_extent

傳回 `extent` 物件，它會捕獲 `tiled_extent` 樣板引數的值 `_Dim0`、`_Dim1`和 `_Dim2`。

### <a name="syntax"></a>語法

```cpp
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>傳回值

`extent` 物件，它會捕獲這個 `tiled_extent` 實例的維度。

## <a name="pad"></a> pad

傳回新的 `tiled_extent` 物件，其中的範圍已調整為要由磚維度平均地整除。

### <a name="syntax"></a>語法

```cpp
tiled_extent pad() const;
```

### <a name="return-value"></a>傳回值

新的 `tiled_extent` 物件，以傳值方式。
## <a name="truncate"></a>截斷

傳回新的 `tiled_extent` 物件，並將範圍向下調整，以供磚維度平均地整除。

### <a name="syntax"></a>語法

```cpp
tiled_extent truncate() const;
```

### <a name="return-value"></a>傳回值

傳回新的 `tiled_extent` 物件，並將範圍向下調整，以供磚維度平均地整除。

## <a name="operator_eq"></a> operator =

將指定 `tiled_index` 物件的內容複寫到這個。

### <a name="syntax"></a>語法

```cpp
tiled_extent&  operator= (
    const tiled_extent& _Other ) restrict (amp, cpu);
```

### <a name="parameters"></a>參數

*_Other*<br/>
要複製的來源 `tiled_index` 物件。

### <a name="return-value"></a>傳回值

這個 `tiled_index` 實例的參考。

## <a name="tile_dim0"></a> tile_dim0

儲存最重要維度的長度。

### <a name="syntax"></a>語法

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a> tile_dim1

儲存下一個最重要維度的長度。

### <a name="syntax"></a>語法

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a> tile_dim2

儲存最不重要維度的長度。

### <a name="syntax"></a>語法

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_extent"></a> tile_extent
  取得 `extent` 物件，其會捕獲 `tiled_extent` 樣板引數的值 `_Dim0`、`_Dim1`和 `_Dim2`。

### <a name="syntax"></a>語法

```cpp
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;
```

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
