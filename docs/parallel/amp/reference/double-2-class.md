---
title: double_2 類別
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::double_2::set_x
- amp_short_vectors/Concurrency::graphics::double_2::operator+=
- amp_short_vectors/Concurrency::graphics::double_2::operator=
- amp_short_vectors/Concurrency::graphics::double_2::operator/=
- amp_short_vectors/Concurrency::graphics::double_2::operator*=
- amp_short_vectors/Concurrency::graphics::double_2::yx
- amp_short_vectors/Concurrency::graphics::double_2::y
- amp_short_vectors/Concurrency::graphics::double_2::xy
- amp_short_vectors/Concurrency::graphics::double_2::set_xy
- amp_short_vectors/Concurrency::graphics::double_2::get_yx
- amp_short_vectors/Concurrency::graphics::double_2::set_yx
- amp_short_vectors/Concurrency::graphics::double_2::get_xy
- amp_short_vectors/Concurrency::graphics::double_2::operator++
- amp_short_vectors/Concurrency::graphics::double_2::get_x
- amp_short_vectors/Concurrency::graphics::double_2::operator-=
- amp_short_vectors/Concurrency::graphics::double_2::rg
- amp_short_vectors/Concurrency::graphics::double_2::gr
- amp_short_vectors/Concurrency::graphics::double_2::get_y
- amp_short_vectors/Concurrency::graphics::double_2::x
- amp_short_vectors/Concurrency::graphics::double_2::r
- amp_short_vectors/Concurrency::graphics::double_2::operator--
- amp_short_vectors/Concurrency::graphics::double_2
- amp_short_vectors/Concurrency::graphics::double_2::operator-
- amp_short_vectors/Concurrency::graphics::double_2::g
- amp_short_vectors/Concurrency::graphics::double_2::set_y
ms.assetid: c19c2d21-3cbf-4ce5-b460-3b8253688f82
ms.openlocfilehash: 73656415d1b8774fe8304d674872524e76ee301d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126704"
---
# <a name="double_2-class"></a>double_2 類別

代表 2 double 的短向量。

## <a name="syntax"></a>語法

```cpp
class double_2;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[double_2 的構造函式](#ctor)|已多載。 預設的處理函式，會使用0初始化所有元素。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|double_2：： get_x||
|double_2：： get_xy||
|double_2：： get_y||
|double_2：： get_yx||
|double_2：： ref_g||
|double_2：： ref_r||
|double_2：： ref_x||
|double_2：： ref_y||
|double_2：： set_x||
|double_2：： set_xy||
|double_2：： set_y||
|double_2：： set_yx||

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|double_2：： operator-||
|double_2：： operator--||
|double_2：： operator * =||
|double_2：： operator/=||
|double_2：： operator + +||
|double_2：： operator + =||
|double_2：： operator =||
|double_2：： operator-=||

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|double_2::size 常數||

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|double_2：： g||
|double_2：： gr||
|double_2：： r||
|double_2：： rg||
|double_2：： x||
|double_2：： xy||
|double_2：： y||
|double_2：： yx||

## <a name="inheritance-hierarchy"></a>繼承階層

`double_2`

## <a name="requirements"></a>需求

**標頭：** amp_short_vectors。h

**命名空間：** Concurrency：： graphics

## <a name="ctor"></a>double_2

預設的處理函式，會使用0初始化所有元素。

```cpp
double_2() restrict(amp,
    cpu);

double_2(
    double _V0,
    double _V1) restrict(amp,
    cpu);

double_2(
    double _V) restrict(amp,
    cpu);

double_2(
    const double_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const norm_2& _Other) restrict(amp,
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

## <a name="double_2__size"></a>容量

```cpp
static const int size = 2;
```

## <a name="see-also"></a>另請參閱

[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)
