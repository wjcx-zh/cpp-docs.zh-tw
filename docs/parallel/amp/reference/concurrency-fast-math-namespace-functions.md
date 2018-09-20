---
title: 'Concurrency:: fast_math 命名空間函式 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- amp_math/Concurrency::fast_math::acos
- amp_math/Concurrency::fast_math::asin
- amp_math/Concurrency::fast_math::asinf
- amp_math/Concurrency::fast_math::atan2
- amp_math/Concurrency::fast_math::atan2f
- amp_math/Concurrency::fast_math::ceil
- amp_math/Concurrency::fast_math::ceilf
- amp_math/Concurrency::fast_math::cosf
- amp_math/Concurrency::fast_math::cosh
- amp_math/Concurrency::fast_math::exp
- amp_math/Concurrency::fast_math::exp2
- amp_math/Concurrency::fast_math::expf
- amp_math/Concurrency::fast_math::fabs
- amp_math/Concurrency::fast_math::floor
- amp_math/Concurrency::fast_math::floorf
- amp_math/Concurrency::fast_math::fmaxf
- amp_math/Concurrency::fast_math::fmin
- amp_math/Concurrency::fast_math::fmod
- amp_math/Concurrency::fast_math::fmodf
- amp_math/Concurrency::fast_math::frexpf
- amp_math/Concurrency::fast_math::isfinite
- amp_math/Concurrency::fast_math::isnan
- amp_math/Concurrency::fast_math::ldexp
- amp_math/Concurrency::fast_math::log
- amp_math/Concurrency::fast_math::log10
- amp_math/Concurrency::fast_math::log2
- amp_math/Concurrency::fast_math::log2f
- amp_math/Concurrency::fast_math::modf
- amp_math/Concurrency::fast_math::modff
- amp_math/Concurrency::fast_math::powf
- amp_math/Concurrency::fast_math::round
- amp_math/Concurrency::fast_math::rsqrt
- amp_math/Concurrency::fast_math::rsqrtf
- amp_math/Concurrency::fast_math::signbitf
- amp_math/Concurrency::fast_math::sin
- amp_math/Concurrency::fast_math::sincosf
- amp_math/Concurrency::fast_math::sinf
- amp_math/Concurrency::fast_math::sinhf
- amp_math/Concurrency::fast_math::sqrt
- amp_math/Concurrency::fast_math::tan
- amp_math/Concurrency::fast_math::tanf
- amp_math/Concurrency::fast_math::tanhf
- amp_math/Concurrency::fast_math::trunc
dev_langs:
- C++
ms.assetid: f5763d62-795b-4de6-a7a5-c7115f158708
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f12ccee2bf282a324fcf4258190240ca8150bb2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446747"
---
# <a name="concurrencyfastmath-namespace-functions"></a>Concurrency:: fast_math 命名空間函式

||||
|-|-|-|
|[acos](#acos)|[acosf](#acosf)|[asin](#asin)|
|[asinf](#asinf)|[atan](#atan)|[atan2](#atan2)|
|[atan2f](#atan2f)|[atanf](#atanf)|[ceil](#ceil)|
|[ceilf](#ceilf)|[cos](#cos)|[cosf](#cosf)|
|[cosh](#cosh)|[coshf](#coshf)|[exp](#exp)|
|[exp2](#exp2)|[exp2f](#exp2f)|[expf](#expf)|
|[fabs](#fabs)|[fabsf](#fabsf)|[floor](#floor)|
|[floorf](#floorf)|[fmax](#fmax)|[fmaxf](#fmaxf)|
|[fmin](#fmin)|[fminf](#fminf)|[fmod](#fmod)|
|[fmodf](#fmodf)|[frexp](#frexp)|[frexpf](#frexpf)|
|[isfinite](#isfinite)|[isinf](#isinf)|[isnan](#isnan)|
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[log](#log)|
|[log10](#log10)|[log10f](#log10f)|[log2](#log2)|
|[log2f](#log2f)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[pow](#pow)|[powf](#powf)|
|[round](#round)|[roundf](#roundf)|[rsqrt](#rsqrt)|
|[rsqrtf](#rsqrtf)|[signbit](#signbit)|[signbitf](#signbitf)|
|[sin](#sin)|[sincos](#sincos)|[sincosf](#sincosf)|
|[sinf](#sinf)|[sinh](#sinh)|[sinhf](#sinhf)|
|[sqrt](#sqrt)|[sqrtf](#sqrtf)|[tan](#tan)|
|[tanf](#tanf)|[tanh](#tanh)|[tanhf](#tanhf)|
|[trunc](#trunc)|[truncf](#truncf)|

##  <a name="acos"></a> acos

計算引數的反餘弦值

```
inline float acos(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反餘弦值

##  <a name="acosf"></a>  acosf

計算引數的反餘弦值

```
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反餘弦值

##  <a name="asin"></a>  asin

計算引數的反正弦值

```
inline float asin(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反正弦值

##  <a name="asinf"></a>  asinf

計算引數的反正弦值

```
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反正弦值

##  <a name="atan"></a>  atan

計算引數的反正切值

```
inline float atan(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反正切值

##  <a name="atan2"></a>  atan2

計算 _Y/_X 的反正切值

```
inline float atan2(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_Y*<br/>
浮點值。

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 _Y/_X 的反正切值

##  <a name="atan2f"></a>  atan2f

計算 _Y/_X 的反正切值

```
inline float atan2f(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_Y*<br/>
浮點值。

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 _Y/_X 的反正切值

##  <a name="atanf"></a>  atanf

計算引數的反正切值

```
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反正切值

##  <a name="ceil"></a>  ceil

計算引數的上限

```
inline float ceil(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的上限

##  <a name="ceilf"></a>  ceilf

計算引數的上限

```
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的上限

##  <a name="cosf"></a>  cosf

計算引數的餘弦函數

```
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的餘弦值

##  <a name="coshf"></a>  coshf

計算引數的雙曲餘弦值

```
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的雙曲餘弦值

##  <a name="cos"></a>  cos

計算引數的餘弦函數

```
inline float cos(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的餘弦值

##  <a name="cosh"></a>  cosh

計算引數的雙曲餘弦值

```
inline float cosh(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的雙曲餘弦值

##  <a name="exp"></a>  exp

計算底數為 e 引數的指數

```
inline float exp(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 e 為底數的指數引數

##  <a name="exp2"></a>  exp2

計算基底 2 指數的引數

```
inline float exp2(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回基底 2 指數的引數

##  <a name="exp2f"></a>  exp2f

計算基底 2 指數的引數

```
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回基底 2 指數的引數

##  <a name="expf"></a>  expf

計算底數為 e 引數的指數

```
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 e 為底數的指數引數

##  <a name="fabs"></a>  fabs

傳回引數的絕對值

```
inline float fabs(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回引數的絕對值

##  <a name="fabsf"></a>  fabsf

傳回引數的絕對值

```
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的絕對值

##  <a name="floor"></a>  floor

計算引數的最小

```
inline float floor(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的下限

##  <a name="floorf"></a>  floorf

計算引數的最小

```
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的下限

##  <a name="fmax"></a>  fmax

判斷引數的最大數值

```
inline float max(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

*_Y*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回的最大的數值引數

##  <a name="fmaxf"></a>  fmaxf

判斷引數的最大數值

```
inline float fmaxf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Y*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回的最大的數值引數

##  <a name="fmin"></a>  fmin

判斷引數的最小數值

```
inline float min(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

*_Y*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回引數的最小數值

##  <a name="fminf"></a>  fminf

判斷引數的最小數值

```
inline float fminf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Y*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的最小數值

##  <a name="fmod"></a>  fmod

計算 _X/_Y 浮點數餘數

```
inline float fmod(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Y*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 _X/_Y 浮點數餘數

##  <a name="fmodf"></a>  fmodf

計算 _X/_Y 浮點數餘數。

```
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Y*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 _X/_Y 浮點數餘數

##  <a name="frexp"></a>  frexp

取得的尾數和指數 _X

```
inline float frexp(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*2^_exp*<br/>
傳回整數的指數 _X 中的浮點值

### <a name="return-value"></a>傳回值

會傳回尾數 _X

##  <a name="frexpf"></a>  frexpf

取得的尾數和指數 _X

```
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*2^_exp*<br/>
傳回整數的指數 _X 中的浮點值

### <a name="return-value"></a>傳回值

會傳回尾數 _X

##  <a name="isfinite"></a>  isfinite

判斷引數值是否有限的值

```
inline int isfinite(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回非零值，才引數具有有限的值

##  <a name="isinf"></a>  isinf

判斷引數是否為無限大的值

```
inline int isinf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回非零值，才引數的無限值

##  <a name="isnan"></a>  isnan

判斷引數是否為 NaN

```
inline int isnan(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回非零值，才引數具有 NaN 值

##  <a name="ldexp"></a>  ldexp

計算出實數從的尾數和指數

```
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值 mentissa

*2^_exp*<br/>
整數指數

### <a name="return-value"></a>傳回值

傳回 _X \* 2 ^ 2^_exp

##  <a name="ldexpf"></a>  ldexpf

計算出實數從的尾數和指數

```
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值 mentissa

*2^_exp*<br/>
整數指數

### <a name="return-value"></a>傳回值

傳回 _X \* 2 ^ 2^_exp

##  <a name="log"></a>  log

計算引數的基底 e 對數

```
inline float log(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的基底 e 對數

##  <a name="log10"></a>  log10

計算引數的基底 10 對數

```
inline float log10(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的基底 10 對數

##  <a name="log10f"></a>  log10f

計算引數的基底 10 對數

```
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的基底 10 對數

##  <a name="log2"></a>  log2

計算引數的基底 2 對數

```
inline float log2(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的基底 2 對數

##  <a name="log2f"></a>  log2f

計算引數的基底 2 對數

```
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的基底 10 對數

##  <a name="logf"></a>  logf

計算引數的基底 e 對數

```
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的基底 e 對數

##  <a name="modf"></a>  modf

將 _X 成小數和整數部分。

```
inline float modf(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*（_i)*<br/>
接收值的整數部分

### <a name="return-value"></a>傳回值

傳回 _X 的帶正負號小數部分

##  <a name="modff"></a>  modff

將 _X 成小數和整數部分。

```
inline float modff(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*（_i)*<br/>
接收值的整數部分

### <a name="return-value"></a>傳回值

傳回 _X 的帶正負號小數部分

##  <a name="pow"></a>  pow

計算 _X 的 _y 次方

```
inline float pow(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值，基底

*_Y*<br/>
浮點數的值指數

### <a name="return-value"></a>傳回值

傳回 _X 的 _y 次方的值

##  <a name="powf"></a>  powf

計算 _X 的 _y 次方

```
inline float powf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值，基底

*_Y*<br/>
浮點數的值指數

### <a name="return-value"></a>傳回值

##  <a name="round"></a>  捨入

會四捨五入為最接近整數的 _X

```
inline float round(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 _X 的最接近的整數

##  <a name="roundf"></a>  roundf

會四捨五入為最接近整數的 _X

```
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 _X 的最接近的整數

##  <a name="rsqrt"></a>  rsqrt

傳回引數的平方根的倒數

```
inline float rsqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的平方根的倒數

##  <a name="rsqrtf"></a>  rsqrtf

傳回引數的平方根的倒數

```
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的平方根的倒數

##  <a name="signbit"></a>  signbit

判斷是否 _X 的正負號負數

```
inline int signbit(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回非零值，才 _X 的正負號為負數

##  <a name="signbitf"></a>  signbitf

判斷是否 _X 的正負號負數

```
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回非零值，才 _X 的正負號為負數

##  <a name="sin"></a>  sin

計算引數的正弦值

```
inline float sin(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的正弦值

##  <a name="sinf"></a>  sinf

計算引數的正弦值

```
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的正弦值

##  <a name="sincos"></a>  sincos

計算 _X 的正弦和餘弦值

```
inline void sincos(
    float _X,
    float* _S,
    float* _C) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_S*<br/>
傳回 _X 的正弦值

*_C*<br/>
傳回 _X 的餘弦值

##  <a name="sincosf"></a>  sincosf

計算 _X 的正弦和餘弦值

```
inline void sincosf(
    float _X,
    float* _S,
    float* _C) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_S*<br/>
傳回 _X 的正弦值

*_C*<br/>
傳回 _X 的餘弦值

##  <a name="sinh"></a>  sinh

計算引數的雙曲正弦值

```
inline float sinh(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的雙曲正弦值

##  <a name="sinhf"></a>  sinhf

計算引數的雙曲正弦值

```
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的雙曲正弦值

##  <a name="sqrt"></a>  sqrt

計算引數的 squre 根目錄

```
inline float sqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的 squre 根項目

##  <a name="sqrtf"></a>  sqrtf

計算引數的 squre 根目錄

```
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的 squre 根項目

##  <a name="tan"></a>  tan

計算引數的正切值

```
inline float tan(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的正切值

##  <a name="tanf"></a>  tanf

計算引數的正切值

```
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的正切值

##  <a name="tanh"></a>  tanh

計算引數的雙曲正切值

```
inline float tanh(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的雙曲正切值

##  <a name="tanhf"></a>  tanhf

計算引數的雙曲正切值

```
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的雙曲正切值

##  <a name="trunc"></a>  trunc

引數截斷成整數部分

```
inline float trunc(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的整數部分

##  <a name="truncf"></a>  truncf

引數截斷成整數部分

```
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的整數部分

## <a name="requirements"></a>需求

**標頭：** amp_math.h**命名空間：** concurrency:: fast_math

## <a name="see-also"></a>另請參閱

[Concurrency::fast_math 命名空間](concurrency-fast-math-namespace.md)
