---
title: unorm 類別
ms.date: 11/04/2016
f1_keywords:
- unorm
- AMP_SHORT_VECTORS/unorm
- AMP_SHORT_VECTORS/Concurrency::graphics::unorm Constructor
ms.assetid: bc30bd20-6452-4d5f-9158-3b11c4c16ed2
ms.openlocfilehash: 7c9ec967be8be618e5f8ab3bad1bfd940bfeaef4
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126301"
---
# <a name="unorm-class"></a>unorm 類別

代表 unorm 數位。 每個元素都是 [0.0 f，1.0 f] 範圍內的浮點數。

## <a name="syntax"></a>語法

```cpp
class unorm;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[unorm 的構造函式](#ctor)|已多載。 預設建構函式。 初始化為 0.0 f。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|unorm：： operator--||
|unorm：： operator float|轉換運算子。 將 unorm 數位轉換成浮點值。|
|unorm：： operator * =||
|unorm：： operator/=||
|unorm：： operator + +||
|unorm：： operator + =||
|unorm：： operator =||
|unorm：： operator-=||

## <a name="inheritance-hierarchy"></a>繼承階層

`unorm`

## <a name="requirements"></a>需求

**標頭：** amp_short_vectors。h

**命名空間：** Concurrency：： graphics

## <a name="ctor"></a>unorm

預設建構函式。 初始化為 0.0 f。

```cpp
unorm(
    void) restrict(amp,
    cpu);

explicit unorm(
    float _V) restrict(amp,
    cpu);

explicit unorm(
    unsigned int _V) restrict(amp,
    cpu);

explicit unorm(
    int _V) restrict(amp,
    cpu);

explicit unorm(
    double _V) restrict(amp,
    cpu);

unorm(
    const unorm& _Other) restrict(amp,
    cpu);

inline explicit unorm(
    const norm& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>參數

*_V*<br/>
用來初始化的值。

*_Other*<br/>
用來初始化的標準物件。

## <a name="see-also"></a>另請參閱

[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)
