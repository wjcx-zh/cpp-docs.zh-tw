---
title: norm 類別
ms.date: 11/04/2016
f1_keywords:
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
ms.openlocfilehash: b5740f33dea6aad79770f77f179803023432248a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447533"
---
# <a name="norm-class"></a>norm 類別

表示標準數位。 每個元素都是 [-1.0 f，1.0 f] 範圍內的浮點數。

## <a name="syntax"></a>語法

```cpp
class norm;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[標準的函式](#ctor)|已多載。 預設建構函式。 初始化為 0.0 f。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|標準：： operator-||
|標準：： operator--||
|標準：：運算子 float|轉換運算子。 將 [標準] 數位轉換成浮點值。|
|標準：： operator * =||
|標準：： operator/=||
|標準：： operator + +||
|標準：： operator + =||
|標準：： operator =||
|標準：： operator-=||

## <a name="inheritance-hierarchy"></a>繼承階層

`norm`

## <a name="requirements"></a>需求

**標頭：** amp_short_vectors。h

**命名空間：** Concurrency：： graphics

## <a name="ctor"></a>標準

預設建構函式。 初始化為 0.0 f。

```cpp
norm(
    void) restrict(amp,
    cpu);

explicit norm(
    float _V) restrict(amp,
    cpu);

explicit norm(
    unsigned int _V) restrict(amp,
    cpu);

explicit norm(
    int _V) restrict(amp,
    cpu);

explicit norm(
    double _V) restrict(amp,
    cpu);

norm(
    const norm& _Other) restrict(amp,
    cpu);

norm(
    const unorm& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>參數

*_V*<br/>
用來初始化的值。

*_Other*<br/>
用來初始化的物件。

## <a name="see-also"></a>另請參閱

[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)
