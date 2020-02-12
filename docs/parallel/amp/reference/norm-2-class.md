---
title: norm_2 類別
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::norm_2::set_x
- amp_short_vectors/Concurrency::graphics::norm_2::set_xy
- amp_short_vectors/Concurrency::graphics::norm_2::g
- amp_short_vectors/Concurrency::graphics::norm_2::get_yx
- amp_short_vectors/Concurrency::graphics::norm_2::set_yx
- amp_short_vectors/Concurrency::graphics::norm_2::operator-=
- amp_short_vectors/Concurrency::graphics::norm_2::operator/=
- amp_short_vectors/Concurrency::graphics::norm_2::operator*=
- amp_short_vectors/Concurrency::graphics::norm_2::yx
- amp_short_vectors/Concurrency::graphics::norm_2::y
- amp_short_vectors/Concurrency::graphics::norm_2::xy
- amp_short_vectors/Concurrency::graphics::norm_2::operator++
- amp_short_vectors/Concurrency::graphics::norm_2::operator-
- amp_short_vectors/Concurrency::graphics::norm_2::rg
- amp_short_vectors/Concurrency::graphics::norm_2::operator=
- amp_short_vectors/Concurrency::graphics::norm_2::get_y
- amp_short_vectors/Concurrency::graphics::norm_2::r
- amp_short_vectors/Concurrency::graphics::norm_2::get_x
- amp_short_vectors/Concurrency::graphics::norm_2::get_xy
- amp_short_vectors/Concurrency::graphics::norm_2::gr
- amp_short_vectors/Concurrency::graphics::norm_2::set_y
- amp_short_vectors/Concurrency::graphics::norm_2::x
- amp_short_vectors/Concurrency::graphics::norm_2::operator+=
- amp_short_vectors/Concurrency::graphics::norm_2
- amp_short_vectors/Concurrency::graphics::norm_2::operator--
ms.assetid: 80703f9b-61f4-414a-93fd-bc774f7d3393
ms.openlocfilehash: 09bd33b5a8d9148c7959f69fcab4a260fe05c332
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126496"
---
# <a name="norm_2-class"></a>norm_2 類別

代表兩個一般數位的短向量。

## <a name="syntax"></a>語法

```cpp
class norm_2;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[norm_2 的構造函式](#ctor)|已多載。 預設的處理函式，會使用0初始化所有元素。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|norm_2：： get_x||
|norm_2：： get_xy||
|norm_2：： get_y||
|norm_2：： get_yx||
|norm_2：： ref_g||
|norm_2：： ref_r||
|norm_2：： ref_x||
|norm_2：： ref_y||
|norm_2：： set_x||
|norm_2：： set_xy||
|norm_2：： set_y||
|norm_2：： set_yx||

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|norm_2：： operator-||
|norm_2：： operator--||
|norm_2：： operator * =||
|norm_2：： operator/=||
|norm_2：： operator + +||
|norm_2：： operator + =||
|norm_2：： operator =||
|norm_2：： operator-=||

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[大小常數](#norm_2__size)||

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|norm_2：： g||
|norm_2：： gr||
|norm_2：： r||
|norm_2：： rg||
|norm_2：： x||
|norm_2：： xy||
|norm_2：： y||
|norm_2：： yx||

## <a name="inheritance-hierarchy"></a>繼承階層

`norm_2`

## <a name="requirements"></a>需求

**標頭：** amp_short_vectors。h

**命名空間：** Concurrency：： graphics

## <a name="ctor"></a>norm_2

預設的處理函式，會使用0初始化所有元素。

```cpp
norm_2() restrict(amp,
    cpu);

norm_2(
    norm _V0,
    norm _V1) restrict(amp,
    cpu);

norm_2(
    float _V0,
    float _V1) restrict(amp,
    cpu);

norm_2(
    unorm _V0,
    unorm _V1) restrict(amp,
    cpu);

norm_2(
    norm _V) restrict(amp,
    cpu);

explicit norm_2(
    float _V) restrict(amp,
    cpu);

norm_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const double_2& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>參數

*_V0*<br/>
要初始化元素0的值。

*_V1*<br/>
要初始化元素1的值。

*_V*<br/>
初始化的值。

*_Other*<br/>
用來初始化的物件。

## <a name="norm_2__size"></a>容量

```cpp
static const int size = 2;
```

## <a name="see-also"></a>另請參閱

[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)
