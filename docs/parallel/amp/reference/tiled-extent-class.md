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
ms.openlocfilehash: ce2710da1a745efedcd6e9e524355eda41e26de2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374716"
---
# <a name="tiled_extent-class"></a>tiled_extent 類別

對`tiled_extent`像是一`extent`到三維的物件,將範圍空間細分為一維、二維或三維切片。

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
最重要的維度的長度。

*_Dim1*<br/>
第二個最重要的維度的長度。

*_Dim2*<br/>
最小尺寸的長度。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[tiled_extent建構函數](#ctor)|將 `tiled_extent` 類別的新執行個體初始化。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[get_tile_extent](#get_tile_extent)|傳`extent``tiled_extent`回捕捉樣本參數`_Dim0`的值的物件`_Dim1`,`_Dim2`與 。|
|[墊](#pad)|返回一個新`tiled_extent`物件,其擴展的擴展區可被切片尺寸均勻整除。|
|[truncate](#truncate)|返回一個新`tiled_extent`物件,其範圍向下調整,以被切片尺寸均勻整除。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[運算子*](#operator_eq)|將指定`tiled_index`物件的內容複製到此物件中。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[tile_dim0常量](#tile_dim0)|存儲最重要的維度的長度。|
|[tile_dim1常量](#tile_dim1)|存儲第二個最重要的維度的長度。|
|[tile_dim2常量](#tile_dim2)|存儲最小尺寸的長度。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[tile_extent](#tile_extent)|取得`extent``tiled_extent`捕捉樣本參數`_Dim0`的值的物件`_Dim1`, 與`_Dim2`。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`extent`

`tiled_extent`

## <a name="requirements"></a>需求

**標頭︰** amp.h

**命名空間：** 並行

## <a name="tiled_extent-constructor"></a><a name="ctor"> </a> tiled_extent建構函數

將 `tiled_extent` 類別的新執行個體初始化。

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
要`extent``tiled_extent`複製的物件。

## <a name="get_tile_extent"></a><a name="get_tile_extent"> </a> get_tile_extent

傳`extent``tiled_extent`回捕捉樣本參數`_Dim0`的值的物件`_Dim1`,`_Dim2`與 。

### <a name="syntax"></a>語法

```cpp
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>傳回值

捕獲`extent``tiled_extent`此 實例維度的物件。

## <a name="pad"></a><a name="pad"> </a>墊

返回一個新`tiled_extent`物件,其擴展的擴展區可被切片尺寸均勻整除。

### <a name="syntax"></a>語法

```cpp
tiled_extent pad() const;
```

### <a name="return-value"></a>傳回值

新`tiled_extent`物件,按值。

## <a name="truncate"></a><a name="truncate"> </a>截流

返回一個新`tiled_extent`物件,其範圍向下調整,以被切片尺寸均勻整除。

### <a name="syntax"></a>語法

```cpp
tiled_extent truncate() const;
```

### <a name="return-value"></a>傳回值

返回一個新`tiled_extent`物件,其範圍向下調整,以被切片尺寸均勻整除。

## <a name="operator"></a><a name="operator_eq"> </a>運算子*

將指定`tiled_index`物件的內容複製到此物件中。

### <a name="syntax"></a>語法

```cpp
tiled_extent&  operator= (
    const tiled_extent& _Other ) restrict (amp, cpu);
```

### <a name="parameters"></a>參數

*_Other*<br/>
要`tiled_index`複製的物件。

### <a name="return-value"></a>傳回值

對此`tiled_index`實例的引用。

## <a name="tile_dim0"></a><a name="tile_dim0"> </a> tile_dim0

存儲最重要的維度的長度。

### <a name="syntax"></a>語法

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tile_dim1"> </a> tile_dim1

存儲第二個最重要的維度的長度。

### <a name="syntax"></a>語法

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tile_dim2"> </a> tile_dim2

存儲最小尺寸的長度。

### <a name="syntax"></a>語法

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_extent"></a><a name="tile_extent"> </a> tile_extent

取得`extent``tiled_extent`捕捉樣本參數`_Dim0`的值的物件`_Dim1`, 與`_Dim2`。

### <a name="syntax"></a>語法

```cpp
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;
```

## <a name="see-also"></a>另請參閱

[併發命名空間(C++ AMP)](concurrency-namespace-cpp-amp.md)
