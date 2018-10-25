---
title: tiled_extent 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 671ecaf8-c7b0-4ac8-bbdc-e30bd92da7c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ffda10923d3be1baf7c9f6ed898480ee1c1367c3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50067692"
---
# <a name="tiledextent-class"></a>tiled_extent 類別

A`tiled_extent`物件是`extent`將範圍空間到一、 二或三維的拼貼一到三個維度的物件。

### <a name="syntax"></a>語法

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

### <a name="parameters"></a>參數

*_Dim0*<br/>
最高有效維度的長度。

*_Dim1*<br/>
下一步 以最高有效維度的長度。

*_Dim2*<br/>
最小顯著性維度的長度。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[tiled_extent 建構函式](#ctor)|初始化 `tiled_extent` 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[get_tile_extent](#get_tile_extent)|傳回`extent`擷取的值的物件`tiled_extent`樣板引數`_Dim0`， `_Dim1`，和`_Dim2`。|
|[pad](#pad)|傳回新`tiled_extent`向上調整為能被 tile 維度整除的範圍的物件。|
|[truncate](#truncate)|傳回新`tiled_extent`向下調整為能被 tile 維度整除的範圍的物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator=](#operator_eq)|將指定的內容複製`tiled_index`到這個物件。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[tile_dim0 常數](#tile_dim0)|儲存的最高有效維度的長度。|
|[tile_dim1 常數](#tile_dim1)|儲存下一步 以最高有效維度的長度。|
|[tile_dim2 常數](#tile_dim2)|儲存最低有效維度的長度。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[tile_extent](#tile_extent)|取得`extent`擷取的值的物件`tiled_extent`樣板引數`_Dim0`， `_Dim1`，和`_Dim2`。|

## <a name="inheritance-hierarchy"></a>繼承階層

`extent`

`tiled_extent`

## <a name="requirements"></a>需求

**標頭︰** amp.h

**命名空間：** 並行

## <a name="ctor"> </a>  tiled_extent 建構函式

初始化 `tiled_extent` 類別的新執行個體。

### <a name="syntax"></a>語法

```
tiled_extent();

tiled_extent(
    const Concurrency::extent<rank>& _Other );

tiled_extent(
    const tiled_extent& _Other );
```

### <a name="parameters"></a>參數

*_Other*<br/>
`extent`或`tiled_extent`来複製的物件。

## <a name="get_tile_extent"> </a>  get_tile_extent

傳回`extent`擷取的值的物件`tiled_extent`樣板引數`_Dim0`， `_Dim1`，和`_Dim2`。

### <a name="syntax"></a>語法

```
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>傳回值

`extent`物件，擷取這個維度`tiled_extent`執行個體。

## <a name="pad"> </a>  填補

傳回新`tiled_extent`向上調整為能被 tile 維度整除的範圍的物件。

### <a name="syntax"></a>語法

```
tiled_extent pad() const;
```

### <a name="return-value"></a>傳回值

新`tiled_extent`物件，依值。
## <a name="truncate"> </a>  截斷

傳回新`tiled_extent`向下調整為能被 tile 維度整除的範圍的物件。

### <a name="syntax"></a>語法

```
tiled_extent truncate() const;
```

### <a name="return-value"></a>傳回值

傳回新`tiled_extent`向下調整為能被 tile 維度整除的範圍的物件。

## <a name="operator_eq"> </a>  運算子 =

將指定的內容複製`tiled_index`到這個物件。

### <a name="syntax"></a>語法

```
tiled_extent&  operator= (
    const tiled_extent& _Other ) restrict (amp, cpu);
```

### <a name="parameters"></a>參數

*_Other*<br/>
`tiled_index`從複製的物件。

### <a name="return-value"></a>傳回值

此參考`tiled_index`執行個體。

## <a name="tile_dim0"> </a>  tile_dim0

儲存的最高有效維度的長度。

### <a name="syntax"></a>語法

```
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"> </a>  tile_dim1

儲存下一步 以最高有效維度的長度。

### <a name="syntax"></a>語法

```
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"> </a>  tile_dim2

儲存最低有效維度的長度。

### <a name="syntax"></a>語法

```
static const int tile_dim2 = _Dim2;
```

## <a name="tile_extent"> </a>  tile_extent
  取得`extent`擷取的值的物件`tiled_extent`樣板引數`_Dim0`， `_Dim1`，和`_Dim2`。

### <a name="syntax"></a>語法

```
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;
```

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
