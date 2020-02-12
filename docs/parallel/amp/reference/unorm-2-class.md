---
title: unorm_2 類別
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator+=
- amp_short_vectors/Concurrency::graphics::unnorm_2::y
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_y
- amp_short_vectors/Concurrency::graphics::unnorm_2::x
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator--
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator*=
- amp_short_vectors/Concurrency::graphics::unnorm_2::xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_y
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator=
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_x
- amp_short_vectors/Concurrency::graphics::unnorm_2::rg
- amp_short_vectors/Concurrency::graphics::unorm_2
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator-=
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator/=
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::gr
- amp_short_vectors/Concurrency::graphics::unnorm_2::r
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator-
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_x
- amp_short_vectors/Concurrency::graphics::unnorm_2::g
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator++
ms.assetid: 62e88ea7-e29f-4f62-95ce-61a1f39f5e34
ms.openlocfilehash: 325a1532a079c8eff9c8dcdc5410dcbfe58fb914
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126197"
---
# <a name="unorm_2-class"></a>unorm_2 類別

代表兩個不帶正負號的一般數位的短向量。

## <a name="syntax"></a>語法

```cpp
class unorm_2;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[unorm_2 的構造函式](#ctor)|已多載。 預設的處理函式，會使用0初始化所有元素。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|unorm_2：： get_x||
|unorm_2：： get_xy||
|unorm_2：： get_y||
|unorm_2：： get_yx||
|unorm_2：： ref_g||
|unorm_2：： ref_r||
|unorm_2：： ref_x||
|unorm_2：： ref_y||
|unorm_2：： set_x||
|unorm_2：： set_xy||
|unorm_2：： set_y||
|unorm_2：： set_yx||

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|unorm_2：： operator--||
|unorm_2：： operator * =||
|unorm_2：： operator/=||
|unorm_2：： operator + +||
|unorm_2：： operator + =||
|unorm_2：： operator =||
|unorm_2：： operator-=||

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|unorm_2::size 常數||

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|unorm_2：： g||
|unorm_2：： gr||
|unorm_2：： r||
|unorm_2：： rg||
|unorm_2：： x||
|unorm_2：： xy||
|unorm_2：： y||
|unorm_2：： yx||

## <a name="inheritance-hierarchy"></a>繼承階層

`unorm_2`

## <a name="requirements"></a>需求

**標頭：** amp_short_vectors。h

**命名空間：** Concurrency：： graphics

## <a name="ctor"></a>unorm_2

預設的處理函式，會使用0初始化所有元素。

```cpp
unorm_2() restrict(amp,
    cpu);

unorm_2(
    unorm _V0,
    unorm _V1) restrict(amp,
    cpu);

unorm_2(
    float _V0,
    float _V1) restrict(amp,
    cpu);

unorm_2(
    unorm _V) restrict(amp,
    cpu);

explicit unorm_2(
    float _V) restrict(amp,
    cpu);

unorm_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
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

## <a name="unorm_2__size"></a>容量

```cpp
static const int size = 2;
```

## <a name="see-also"></a>另請參閱

[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)
