---
title: norm 類別
ms.date: 11/04/2016
f1_keywords:
- norm
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
ms.openlocfilehash: 56f879ef2fc0d3010ab4f64fedaf2570dac565d1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272421"
---
# <a name="norm-class"></a>norm 類別

代表範數字。 每個項目是浮點數字範圍內的 [-1.0 f、 1.0f]。

## <a name="syntax"></a>語法

```
class norm;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[norm 建構函式](#ctor)|多載。 預設建構函式。 將初始化為 0.0。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|norm::operator-||
|norm::operator--||
|norm::operator float|轉換運算子。 將範數字轉換成浮點值。|
|norm::operator*=||
|norm::operator/=||
|norm::operator++||
|norm::operator+=||
|norm::operator=||
|norm::operator-=||

## <a name="inheritance-hierarchy"></a>繼承階層

`norm`

## <a name="requirements"></a>需求

**標頭：** amp_short_vectors.h

**命名空間：** Concurrency:: graphics

##  <a name="ctor"></a> norm

預設建構函式。 將初始化為 0.0。

```
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
