---
title: int_2 類別
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::int_2::y
- amp_short_vectors/Concurrency::graphics::int_2::set_x
- amp_short_vectors/Concurrency::graphics::int_2::set_y
- amp_short_vectors/Concurrency::graphics::int_2::get_yx
- amp_short_vectors/Concurrency::graphics::int_2::operator++
- amp_short_vectors/Concurrency::graphics::int_2::x
- amp_short_vectors/Concurrency::graphics::int_2::set_yx
- amp_short_vectors/Concurrency::graphics::int_2::operator/=
- amp_short_vectors/Concurrency::graphics::int_2::get_y
- amp_short_vectors/Concurrency::graphics::int_2::gr
- amp_short_vectors/Concurrency::graphics::int_2::operator*=
- amp_short_vectors/Concurrency::graphics::int_2::r
- amp_short_vectors/Concurrency::graphics::int_2::get_xy
- amp_short_vectors/Concurrency::graphics::int_2::operator=
- amp_short_vectors/Concurrency::graphics::int_2::g
- amp_short_vectors/Concurrency::graphics::int_2::rg
- amp_short_vectors/Concurrency::graphics::int_2::xy
- amp_short_vectors/Concurrency::graphics::int_2::operator-=
- amp_short_vectors/Concurrency::graphics::int_2::get_x
- amp_short_vectors/Concurrency::graphics::int_2::yx
- amp_short_vectors/Concurrency::graphics::int_2
- amp_short_vectors/Concurrency::graphics::int_2::operator-
- amp_short_vectors/Concurrency::graphics::int_2::set_xy
- amp_short_vectors/Concurrency::graphics::int_2::operator+=
- amp_short_vectors/Concurrency::graphics::int_2::operator--
ms.assetid: 258b02e9-f1ee-46c2-8edd-dc9f69184846
ms.openlocfilehash: 000bda3a6ecc5b1ebf9be4e07ce8d703b6cd9194
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126639"
---
# <a name="int_2-class"></a>int_2 類別

表示兩個整數的短向量。

## <a name="syntax"></a>語法

```cpp
class int_2;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[int_2 的構造函式](#ctor)|已多載。 預設的處理函式，會使用0初始化所有元素。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|int_2：： get_x||
|int_2：： get_xy||
|int_2：： get_y||
|int_2：： get_yx||
|int_2：： ref_g||
|int_2：： ref_r||
|int_2：： ref_x||
|int_2：： ref_y||
|int_2：： set_x||
|int_2：： set_xy||
|int_2：： set_y||
|int_2：： set_yx||

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|int_2：： operator-||
|int_2：： operator--||
|int_2：： operator% =||
|int_2：： operator & =||
|int_2：： operator * =||
|int_2：： operator/=||
|int_2：： operator ^ =||
|int_2：： operator&#124;=||
|int_2：： operator ~||
|int_2：： operator + +||
|int_2：： operator + =||
|int_2：： operator <\<=||
|int_2：： operator =||
|int_2：： operator-=||
|int_2：： operator > > =||

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[大小常數](#int_2__size)||

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|int_2：： g||
|int_2：： gr||
|int_2：： r||
|int_2：： rg||
|int_2：： x||
|int_2：： xy||
|int_2：： y||
|int_2：： yx||

## <a name="inheritance-hierarchy"></a>繼承階層

`int_2`

## <a name="requirements"></a>需求

**標頭：** amp_short_vectors。h

**命名空間：** Concurrency：： graphics

## <a name="ctor"></a>int_2

預設的處理函式，會使用0初始化所有元素。

```cpp
int_2() restrict(amp,
    cpu);

int_2(
    int _V0,
    int _V1) restrict(amp,
    cpu);

int_2(
    int _V) restrict(amp,
    cpu);

int_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline int_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline int_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline int_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline int_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline int_2(
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

## <a name="int_2__size"></a>容量

```cpp
static const int size = 2;
```

## <a name="see-also"></a>另請參閱

[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)
