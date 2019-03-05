---
title: unorm 類別
ms.date: 11/04/2016
f1_keywords:
- unorm
- AMP_SHORT_VECTORS/unorm
- AMP_SHORT_VECTORS/Concurrency::graphics::unorm Constructor
ms.assetid: bc30bd20-6452-4d5f-9158-3b11c4c16ed2
ms.openlocfilehash: 059cd3a388d67e540a91146f2a287c375fb02bd1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300800"
---
# <a name="unorm-class"></a>unorm 類別

代表 unorm 數字。 每個項目是浮點數中的範圍 [0.0，1.0 f]。

## <a name="syntax"></a>語法

```
class unorm;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[unorm 建構函式](#ctor)|多載。 預設建構函式。 將初始化為 0.0。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|unorm::operator--||
|unorm::operator float|轉換運算子。 將 unorm 號碼轉換為浮點值。|
|unorm::operator*=||
|unorm::operator/=||
|unorm::operator++||
|unorm::operator+=||
|unorm::operator=||
|unorm::operator-=||

## <a name="inheritance-hierarchy"></a>繼承階層

`unorm`

## <a name="requirements"></a>需求

**標頭：** amp_short_vectors.h

**命名空間：** Concurrency:: graphics

##  <a name="ctor"></a> unorm

預設建構函式。 將初始化為 0.0。

```
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
Norm 物件，用來初始化。

## <a name="see-also"></a>另請參閱

[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)
