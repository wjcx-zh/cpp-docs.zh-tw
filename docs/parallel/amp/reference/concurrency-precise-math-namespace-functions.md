---
title: Concurrency::precise_math 命名空間函式
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::precise_math::acos
- amp_math/Concurrency::precise_math::acosh
- amp_math/Concurrency::precise_math::acoshf
- amp_math/Concurrency::precise_math::asinf
- amp_math/Concurrency::precise_math::asinh
- amp_math/Concurrency::precise_math::atan
- amp_math/Concurrency::precise_math::atan2
- amp_math/Concurrency::precise_math::atanf
- amp_math/Concurrency::precise_math::atanh
- amp_math/Concurrency::precise_math::cbrt
- amp_math/Concurrency::precise_math::cbrtf
- amp_math/Concurrency::precise_math::ceilf
- amp_math/Concurrency::precise_math::copysign
- amp_math/Concurrency::precise_math::cos
- amp_math/Concurrency::precise_math::cosf
- amp_math/Concurrency::precise_math::coshf
- amp_math/Concurrency::precise_math::cospi
- amp_math/Concurrency::precise_math::erf
- amp_math/Concurrency::precise_math::erfc
- amp_math/Concurrency::precise_math::erfcinv
- amp_math/Concurrency::precise_math::erfcinvf
- amp_math/Concurrency::precise_math::erfinv
- amp_math/Concurrency::precise_math::erfinvf
- amp_math/Concurrency::precise_math::exp10
- amp_math/Concurrency::precise_math::exp10f
- amp_math/Concurrency::precise_math::exp2f
- amp_math/Concurrency::precise_math::expf
- amp_math/Concurrency::precise_math::expm1f
- amp_math/Concurrency::precise_math::fabs
- amp_math/Concurrency::precise_math::floor
- amp_math/Concurrency::precise_math::fdim
- amp_math/Concurrency::precise_math::floorf
- amp_math/Concurrency::precise_math::fmaf
- amp_math/Concurrency::precise_math::fmaxf
- amp_math/Concurrency::precise_math::fmin
- amp_math/Concurrency::precise_math::fmod
- amp_math/Concurrency::precise_math::fmodf
- amp_math/Concurrency::precise_math::frexp
- amp_math/Concurrency::precise_math::frexpf
- amp_math/Concurrency::precise_math::hypotf
- amp_math/Concurrency::precise_math::ilogb
- amp_math/Concurrency::precise_math::isfinite
- amp_math/Concurrency::precise_math::isinf
- amp_math/Concurrency::precise_math::isnormal
- amp_math/Concurrency::precise_math::ldexp
- amp_math/Concurrency::precise_math::lgamma
- amp_math/Concurrency::precise_math::lgammaf
- amp_math/Concurrency::precise_math::log10
- amp_math/Concurrency::precise_math::log10f
- amp_math/Concurrency::precise_math::log1pf
- amp_math/Concurrency::precise_math::log2
- amp_math/Concurrency::precise_math::logb
- amp_math/Concurrency::precise_math::logbf
- amp_math/Concurrency::precise_math::modf
- amp_math/Concurrency::precise_math::modff
- amp_math/Concurrency::precise_math::nanf
- amp_math/Concurrency::precise_math::nearbyint
- amp_math/Concurrency::precise_math::nextafter
- amp_math/Concurrency::precise_math::nextafterf
- amp_math/Concurrency::precise_math::phif
- amp_math/Concurrency::precise_math::pow
- amp_math/Concurrency::precise_math::probit
- amp_math/Concurrency::precise_math::probitf
- amp_math/Concurrency::precise_math::rcbrtf
- amp_math/Concurrency::precise_math::remainder
- amp_math/Concurrency::precise_math::remquo
- amp_math/Concurrency::precise_math::remquof
- amp_math/Concurrency::precise_math::roundf
- amp_math/Concurrency::precise_math::rsqrt
- amp_math/Concurrency::precise_math::scalb
- amp_math/Concurrency::precise_math::scalbf
- amp_math/Concurrency::precise_math::scalbnf
- amp_math/Concurrency::precise_math::signbit
- amp_math/Concurrency::precise_math::sin
- amp_math/Concurrency::precise_math::sincos
- amp_math/Concurrency::precise_math::sinf
- amp_math/Concurrency::precise_math::sinh
- amp_math/Concurrency::precise_math::sinpi
- amp_math/Concurrency::precise_math::sinpif
- amp_math/Concurrency::precise_math::sqrtf
- amp_math/Concurrency::precise_math::tan
- amp_math/Concurrency::precise_math::tanh
- amp_math/Concurrency::precise_math::tanhf
- amp_math/Concurrency::precise_math::tanpif
- amp_math/Concurrency::precise_math::tgamma
- amp_math/Concurrency::precise_math::trunc
- amp_math/Concurrency::precise_math::truncf
ms.assetid: fae53ab4-d1c5-45bb-a6a0-a74258e9aea3
ms.openlocfilehash: 53ebaf8d9cc1bca53b1fe51464668d6df8e08424
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126939"
---
# <a name="concurrencyprecise_math-namespace-functions"></a>Concurrency::precise_math 命名空間函式

||||
|-|-|-|
|[acos](#acos)|[acosf](#acosf)|[acosh](#acosh)|
|[acoshf](#acoshf)|[asin](#asin)|[asinf](#asinf)|
|[asinh](#asinh)|[asinhf](#asinhf)|[atan](#atan)|
|[atan2](#atan2)|[atan2f](#atan2f)|[atanf](#atanf)|
|[atanh](#atanh)|[atanhf](#atanhf)|[cbrt](#cbrt)|
|[cbrtf](#cbrtf)|[ceil](#ceil)|[ceilf](#ceilf)|
|[copysign](#copysign)|[copysignf](#copysignf)|[cos](#cos)|
|[cosf](#cosf)|[cosh](#cosh)|[coshf](#coshf)|
|[cospi](#cospi)|[cospif](#cospif)|[erf](#erf)|
|[erfc](#erfc)|[erfcf](#erfcf)|[erfcinv](#erfcinv)|
|[erfcinvf](#erfcinvf)|[erff](#erff)|[erfinv](#erfinv)|
|[erfinvf](#erfinvf)|[exp](#exp)|[exp10](#exp10)|
|[exp10f](#exp10f)|[exp2](#exp2)|[exp2f](#exp2f)|
|[expf](#expf)|[expm1](#expm1)|[expm1f](#expm1f)|
|[fabs](#fabs)|[fabsf](#fabsf)|[floor](#floor)|
|[fdim](#fdim)|[fdimf](#fdimf)||
|[floorf](#floorf)|[fma](#fma)|[fmaf](#fmaf)|
[fmax](#fmax)|[fmaxf](#fmaxf)||
|[fmin](#fmin)|[fminf](#fminf)|[fmod](#fmod)|
|[fmodf](#fmodf)|[fpclassify](#fpclassify)|[frexp](#frexp)|
|[frexpf](#frexpf)|[hypot](#hypot)|[hypotf](#hypotf)|
|[ilogb](#ilogb)|[ilogbf](#ilogbf)|[isfinite](#isfinite)|
|[isinf](#isinf)|[isnan](#isnan)|[isnormal](#isnormal)|
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[lgamma](#lgamma)|
|[lgammaf](#lgammaf)|[log](#log)|[log10](#log10)|
|[log10f](#log10f)|[log1p](#log1p)|[log1pf](#log1pf)|
|[log2](#log2)|[log2f](#log2f)|[logb](#logb)|
|[logbf](#logbf)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[nan](#nan)|[nanf](#nanf)|
|[nearbyint](#nearbyint)|[nearbyintf](#nearbyintf)|[nextafter](#nextafter)|
|[nextafterf](#nextafterf)|[phi](#phi)|[phif](#phif)|
|[pow](#pow)|[powf](#powf)|[probit](#probit)|
|[probitf](#probitf)|[rcbrt](#rcbrt)|[rcbrtf](#rcbrtf)|
|[remainder](#remainder)|[remainderf](#remainderf)|[remquo](#remquo)|
|[remquof](#remquof)|[round](#round)|[roundf](#roundf)|
|[rsqrt](#rsqrt)|[rsqrtf](#rsqrtf)|[scalb](#scalb)|
|[scalbf](#scalbf)|[scalbn](#scalbn)|[scalbnf](#scalbnf)|
|[signbit](#signbit)|[signbitf](#signbitf)|[sin](#sin)|
|[sincos](#sincos)|[sincosf](#sincosf)|[sinf](#sinf)|
|[sinh](#sinh)|[sinhf](#sinhf)|[sinpi](#sinpi)|
|[sinpif](#sinpif)|[sqrt](#sqrt)|[sqrtf](#sqrtf)|
|[tan](#tan)|[tanf](#tanf)|[tanh](#tanh)|
|[tanhf](#tanhf)|[tanpi](#tanpi)|[tanpif](#tanpif)|
|[tgamma](#tgamma)|[tgammaf](#tgammaf)|[trunc](#trunc)|
|[truncf](#truncf)|

## <a name="acos"></a> acos

計算引數的反余弦

```cpp
inline float acos(float _X) restrict(amp);

inline double acos(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反余弦值。

## <a name="acosf"></a>acosf

計算引數的反余弦

```cpp
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反余弦值。

## <a name="acosh"></a>acosh

計算引數的反雙曲余弦值

```cpp
inline float acosh(float _X) restrict(amp);

inline double acosh(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反雙曲余弦值。

## <a name="acoshf"></a>acoshf

計算引數的反雙曲余弦值

```cpp
inline float acoshf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反雙曲余弦值。

## <a name="asin"></a>  asin

計算引數的反正弦

```cpp
inline float asin(float _X) restrict(amp);

inline double asin(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反正弦值

## <a name="asinf"></a>asinf

計算引數的反正弦

```cpp
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反正弦值

## <a name="asinh"></a>asinh

計算引數的反雙曲正弦值

```cpp
inline float asinh(float _X) restrict(amp);

inline double asinh(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反雙曲正弦值。

## <a name="asinhf"></a>asinhf

計算引數的反雙曲正弦值

```cpp
inline float asinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反雙曲正弦值。

## <a name="atan"></a>  atan

計算引數的反正切

```cpp
inline float atan(float _X) restrict(amp);

inline double atan(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反正切值。

## <a name="atan2"></a>  atan2

計算 _Y/_X 的反正切值

```cpp
inline float atan2(
    float _Y,
    float _X) restrict(amp);

inline double atan2(
    double _Y,
    double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_Y*<br/>
浮點值。

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 _Y/_X 的反正切值

## <a name="atan2f"></a>atan2f

計算 _Y/_X 的反正切值

```cpp
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

## <a name="atanf"></a>atanf

計算引數的反正切

```cpp
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反正切值。

## <a name="atanh"></a>atanh

計算引數的反雙曲正切函數

```cpp
inline float atanh(float _X) restrict(amp);

inline double atanh(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反雙曲正切值。

## <a name="atanhf"></a>atanhf

計算引數的反雙曲正切函數

```cpp
inline float atanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反雙曲正切值。

## <a name="cbrt"></a>cbrt

計算引數的實際 cube 根目錄

```cpp
inline float cbrt(float _X) restrict(amp);

inline double cbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的實際 cube 根目錄

## <a name="cbrtf"></a>cbrtf

計算引數的實際 cube 根目錄

```cpp
inline float cbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的實際 cube 根目錄

## <a name="ceil"></a>ceil

計算引數的上限

```cpp
inline float ceil(float _X) restrict(amp);

inline double ceil(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的上限

## <a name="ceilf"></a>ceilf

計算引數的上限

```cpp
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的上限

## <a name="copysign"></a>copysign

產生具有 _X 大小和正負號的值 _Y

```cpp
inline float copysign(
    float _X,
    float _Y) restrict(amp);

inline double copysign(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Y*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回值，其大小為 _X，而的正負號為 _Y

## <a name="copysignf"></a>copysignf

產生具有 _X 大小和正負號的值 _Y

```cpp
inline float copysignf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Y*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回值，其大小為 _X，而的正負號為 _Y

## <a name="cos"></a>  cos

計算引數的餘弦

```cpp
inline float cos(float _X) restrict(amp);

inline double cos(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的余弦值。

## <a name="cosf"></a>cosf

計算引數的餘弦

```cpp
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的余弦值。

## <a name="cosh"></a>  cosh

計算引數的雙曲余弦值

```cpp
inline float cosh(float _X) restrict(amp);

inline double cosh(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的雙曲余弦值

## <a name="coshf"></a>coshf

計算引數的雙曲余弦值

```cpp
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的雙曲余弦值

## <a name="cospi"></a>cospi

計算 pi \* 的余弦值 _X

```cpp
inline float cospi(float _X) restrict(amp);

inline double cospi(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 pi \* 的余弦值 _X

## <a name="cospif"></a>cospif

計算 pi \* 的余弦值 _X

```cpp
inline float cospif(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 pi \* 的余弦值 _X

## <a name="erf"></a>erf

計算的錯誤函數 _X

```cpp
inline float erf(float _X) restrict(amp);

inline double erf(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回的錯誤函式 _X

## <a name="erfc"></a>erfc

計算的互補誤差函數 _X

```cpp
inline float erfc(float _X) restrict(amp);

inline double erfc(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回的互補誤差函數 _X

## <a name="erfcf"></a>erfcf

計算的互補誤差函數 _X

```cpp
inline float erfcf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回的互補誤差函數 _X

## <a name="erfcinv"></a>erfcinv

計算的反向互補誤差函數 _X

```cpp
inline float erfcinv(float _X) restrict(amp);

inline double erfcinv(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回的反向互補誤差函數 _X

## <a name="erfcinvf"></a>erfcinvf

計算的反向互補誤差函數 _X

```cpp
inline float erfcinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回的反向互補誤差函數 _X

## <a name="erff"></a>erff

計算的錯誤函數 _X

```cpp
inline float erff(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回的錯誤函式 _X

## <a name="erfinv"></a>erfinv

計算的反向錯誤函數 _X

```cpp
inline float erfinv(float _X) restrict(amp);

inline double erfinv(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回的反向錯誤函數 _X

## <a name="erfinvf"></a>erfinvf

計算的反向錯誤函數 _X

```cpp
inline float erfinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回的反向錯誤函數 _X

## <a name="exp10"></a>exp10

計算引數的以10為底數的指數

```cpp
inline float exp10(float _X) restrict(amp);

inline double exp10(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的以10為底數的指數

## <a name="exp10f"></a>exp10f

計算引數的以10為底數的指數

```cpp
inline float exp10f(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的以10為底數的指數

## <a name="expm1"></a>expm1

計算引數以 e 為底數的指數，減 1。

```cpp
inline float expm1(float exponent) restrict(amp);

inline double expm1(double exponent) restrict(amp);
```

### <a name="parameters"></a>參數

*加*<br/>
數學運算式的指數詞彙*n* `e`<sup>n</sup>，其中 `e` 是自然對數的基底。

### <a name="return-value"></a>傳回值

傳回引數以 e 為底數的指數，減 1。

## <a name="expm1f"></a>expm1f

計算引數以 e 為底數的指數，減 1。

```cpp
inline float expm1f(float exponent) restrict(amp);
```

### <a name="parameters"></a>參數

*加*<br/>
數學運算式的指數詞彙*n* `e`<sup>n</sup>，其中 `e` 是自然對數的基底。

### <a name="return-value"></a>傳回值

傳回引數以 e 為底數的指數，減 1。

## <a name="exp"></a>  exp

計算引數的以 e 為底數的指數

```cpp
inline float exp(float _X) restrict(amp);

inline double exp(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的以 e 為底數的指數

## <a name="expf"></a>expf

計算引數的以 e 為底數的指數

```cpp
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的以 e 為底數的指數

## <a name="exp2"></a>exp2

計算引數的基底2指數

```cpp
inline float exp2(float _X) restrict(amp);

inline double exp2(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的基底 2 指數

## <a name="exp2f"></a>exp2f

計算引數的基底2指數

```cpp
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的基底 2 指數

## <a name="fabs"></a>fabs

傳回引數的絕對值。

```cpp
inline float fabs(float _X) restrict(amp);

inline double fabs(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的絕對值。

## <a name="fabsf"></a>fabsf

傳回引數的絕對值。

```cpp
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的絕對值。

## <a name="fdim"></a>fdim

計算引數之間的正差。

```cpp
inline float fdim(
   float _X,
   float _Y
) restrict(amp);
inline double fdim(
   double _X,
   double _Y
) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值 *_Y*<br/>
浮點值。

### <a name="return-value"></a>傳回值

如果 _X 大於 _Y，_X 和 _Y 之間的差異;否則為 + 0。

## <a name="fdimf"></a>fdimf

計算引數之間的正差。

```cpp
inline float fdimf(
   float _X,
   float _Y
) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值 *_Y*<br/>
浮點值。

### <a name="return-value"></a>傳回值

如果 _X 大於 _Y，_X 和 _Y 之間的差異;否則為 + 0。

## <a name="floor"></a>車間

計算引數的樓層

```cpp
inline float floor(float _X) restrict(amp);

inline double floor(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的基底

## <a name="floorf"></a>floorf

計算引數的樓層

```cpp
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的基底

## <a name="a-namefma-fma"></a><a name="fma"> fma

計算第一個和第二個指定引數的乘積，然後將第三個指定的引數加入至結果。整個計算會當做單一作業來執行。

```cpp
inline float fma(
   float _X,
   float _Y,
   float _Z
) restrict(amp);

inline double fma(
   double _X,
   double _Y,
   double _Z
) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
第一個浮點引數。
*_Y*<br/>
第二個浮點引數。
*_Z*<br/>
第三個浮點引數。

### <a name="return-value"></a>傳回值

運算式的結果（_X \* _Y） + _Z。 整個計算會當做單一作業來執行;也就是說，子運算式會計算為無限精確度，而且只會四捨五入最終結果。

## <a name="fmaf"></a>fmaf

計算第一個和第二個指定引數的乘積，然後將第三個指定的引數加入至結果。整個計算會當做單一作業來執行。

```cpp
inline float fmaf(
   float _X,
   float _Y,
   float _Z
) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
第一個浮點引數。
*_Y*<br/>
第二個浮點引數。
*_Z*<br/>
第三個浮點引數。

### <a name="return-value"></a>傳回值

運算式的結果（_X \* _Y） + _Z。 整個計算會當做單一作業來執行;也就是說，子運算式會計算為無限精確度，而且只會四捨五入最終結果。

## <a name="fmax"></a>fmax

判斷引數的最大數值

```cpp
inline float fmax(
    float _X,
    float _Y) restrict(amp);

inline double fmax(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Y*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的最大數值

## <a name="fmaxf"></a>fmaxf

判斷引數的最大數值

```cpp
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

傳回引數的最大數值

## <a name="fmin"></a>fmin

判斷引數的最小數值

```cpp
inline float fmin(
    float _X,
    float _Y) restrict(amp);

inline double fmin(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Y*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的最小數值

## <a name="fminf"></a>fminf

判斷引數的最小數值

```cpp
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

## <a name="fmod"></a>fmod 函式C++ （AMP）

計算第一個指定引數除以第二個指定引數的餘數。

```cpp
inline float fmod(
    float _X,
    float _Y) restrict(amp);

inline double fmod(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
第一個浮點引數。

*_Y*<br/>
第二個浮點引數。

### <a name="return-value"></a>傳回值

`_X` 的餘數除以 `_Y`;也就是 `_X`的值  - `_Y`*n*，其中*n*是整數，因此  - *n*的 `_X`大小 `_Y`小於 `_Y`的大小。

## <a name="fmodf"></a>fmodf

計算第一個指定引數除以第二個指定引數的餘數。

```cpp
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
第一個浮點引數。

*_Y*<br/>
第二個浮點引數。

### <a name="return-value"></a>傳回值

`_X` 的餘數除以 `_Y`;也就是 `_X`的值  - `_Y`*n*，其中*n*是整數，因此  - *n*的 `_X`大小 `_Y`小於 `_Y`的大小。

## <a name="fpclassify"></a>fpclassify

將引數值分類為 NaN、無限大、normal、偏低、零

```cpp
inline int fpclassify(float _X) restrict(amp);

inline int fpclassify(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回適用于引數值的數位分類宏的值。

## <a name="frexp"></a>frexp

取得 _X 的尾數和指數

```cpp
inline float frexp(
    float _X,
    _Out_ int* _Exp) restrict(amp);

inline double frexp(
    double _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Exp*<br/>
以浮點值傳回 _X 的整數指數

### <a name="return-value"></a>傳回值

傳回尾數 _X

## <a name="frexpf"></a>frexpf

取得 _X 的尾數和指數

```cpp
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Exp*<br/>
以浮點值傳回 _X 的整數指數

### <a name="return-value"></a>傳回值

傳回尾數 _X

## <a name="hypot"></a>hypot

計算 _X 和 _Y 的平方總和的平方根。

```cpp
inline float hypot(
    float _X,
    float _Y) restrict(amp);

inline double hypot(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Y*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 _X 和 _Y 的平方總和的平方根。

## <a name="hypotf"></a>hypotf

計算 _X 和 _Y 的平方總和的平方根。

```cpp
inline float hypotf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Y*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 _X 和 _Y 的平方總和的平方根。

## <a name="ilogb"></a>ilogb

將 _X 的指數解壓縮為帶正負號的 int 值

```cpp
inline int ilogb(float _X) restrict(amp);

inline int ilogb(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

以帶正負號的 int 值傳回 _X 的指數

## <a name="ilogbf"></a>ilogbf

將 _X 的指數解壓縮為帶正負號的 int 值

```cpp
inline int ilogbf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

以帶正負號的 int 值傳回 _X 的指數

## <a name="isfinite"></a>isfinite

判斷引數是否有有限值

```cpp
inline int isfinite(float _X) restrict(amp);

inline int isfinite(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

只有在引數具有有限值時，才會傳回非零值

## <a name="isinf"></a>isinf

判斷引數是否為無限大

```cpp
inline int isinf(float _X) restrict(amp);

inline int isinf(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

只有在引數具有無限值時，才會傳回非零值

## <a name="isnan"></a>isnan

判斷引數是否為 NaN

```cpp
inline int isnan(float _X) restrict(amp);

inline int isnan(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

只有在引數具有 NaN 值時，才會傳回非零值

## <a name="isnormal"></a>isnormal

判斷引數是否為正常的

```cpp
inline int isnormal(float _X) restrict(amp);

inline int isnormal(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

只有在引數具有一般值時，才會傳回非零值

## <a name="ldexp"></a>ldexp

計算指定之尾數和指數中的實數。

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);

inline double ldexp(
    double _X,
    double _Exp) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值，尾數

*_Exp*<br/>
整數值，指數

### <a name="return-value"></a>傳回值

傳回 _X \* 2 ^ _Exp

## <a name="ldexpf"></a>ldexpf

計算指定之尾數和指數中的實數。

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值，尾數

*_Exp*<br/>
整數值，指數

### <a name="return-value"></a>傳回值

傳回 _X \* 2 ^ _Exp

## <a name="lgamma"></a>lgamma

計算引數的 gamma 絕對值的自然對數

```cpp
inline float lgamma(
    float _X,
    _Out_ int* _Sign) restrict(amp);

inline double lgamma(
    double _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Sign*<br/>
傳回正負號

### <a name="return-value"></a>傳回值

傳回引數之 gamma 絕對值的自然對數

## <a name="lgammaf"></a>lgammaf

計算引數的 gamma 絕對值的自然對數

```cpp
inline float lgammaf(
    float _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Sign*<br/>
傳回正負號

### <a name="return-value"></a>傳回值

傳回引數之 gamma 絕對值的自然對數

## <a name="log"></a>  log

計算引數的以 e 為底數的對數

```cpp
inline float log(float _X) restrict(amp);

inline double log(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的以 e 為底數的對數

## <a name="log10"></a>  log10

計算引數的以10為底數的對數

```cpp
inline float log10(float _X) restrict(amp);

inline double log10(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的以10為底數的對數

## <a name="log10f"></a>log10f

計算引數的以10為底數的對數

```cpp
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的以10為底數的對數

## <a name="log1p"></a>log1p

計算1加上引數的以 e 為底數的對數

```cpp
inline float log1p(float _X) restrict(amp);

inline double log1p(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回1加上引數的以 e 為底數的對數

## <a name="log1pf"></a>log1pf

計算1加上引數的以 e 為底數的對數

```cpp
inline float log1pf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回1加上引數的以 e 為底數的對數

## <a name="log2"></a>log2

計算引數的以2為底數的對數

```cpp
inline float log2(float _X) restrict(amp);

inline double log2(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的以10為底數的對數

## <a name="log2f"></a>log2f

計算引數的以2為底數的對數

```cpp
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的以10為底數的對數

## <a name="logb"></a>logb

以浮點格式將 _X 的指數解壓縮為帶正負號的整數值

```cpp
inline float logb(float _X) restrict(amp);

inline double logb(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 _X 的帶正負號的指數

## <a name="logbf"></a>logbf

以浮點格式將 _X 的指數解壓縮為帶正負號的整數值

```cpp
inline float logbf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 _X 的帶正負號的指數

## <a name="logf"></a>logf

計算引數的以 e 為底數的對數

```cpp
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的以 e 為底數的對數

## <a name="modf"></a>modf

將指定的引數分割成小數和整數部分。

```cpp
inline float modf(
    float _X,
    _Out_ float* _Iptr) restrict(amp);

inline double modf(
    double _X,
    _Out_ double* _Iptr) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Iptr*<br/>
脫銷`_X`的整數部分（以浮點值為起點）。

### <a name="return-value"></a>傳回值

`_X`的帶正負號小數部分。

## <a name="modff"></a>modff

將指定的引數分割成小數和整數部分。

```cpp
inline float modff(
    float _X,
    _Out_ float* _Iptr) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Iptr*<br/>
`_X`的整數部分（以浮點值為起點）。

### <a name="return-value"></a>傳回值

傳回 `_X`的帶正負號小數部分。

## <a name="nan"></a>nan

傳回無訊息 NaN

```cpp
inline double nan(int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回無訊息 NaN （如果有的話），以及中所指出的內容 _X

## <a name="nanf"></a>nanf

傳回無訊息 NaN

```cpp
inline float nanf(int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回無訊息 NaN （如果有的話），以及中所指出的內容 _X

## <a name="nearbyint"></a>nearbyint

使用目前的進位方向，將引數四捨五入成浮點格式的整數值。

```cpp
inline float nearbyint(float _X) restrict(amp);

inline double nearbyint(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回四捨五入的整數值。

## <a name="nearbyintf"></a>nearbyintf

使用目前的進位方向，將引數四捨五入成浮點格式的整數值。

```cpp
inline float nearbyintf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回四捨五入的整數值。

## <a name="nextafter"></a>nextafter

以 _Y 的方向 _X 之後，在函式的類型中判斷下一個能顯示的值

```cpp
inline float nextafter(
    float _X,
    float _Y) restrict(amp);

inline double nextafter(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Y*<br/>
浮點值。

### <a name="return-value"></a>傳回值

在函式的 _Y 中 _X 之後，傳回下一個顯示的值（在函數的類型中）

## <a name="nextafterf"></a>nextafterf

以 _Y 的方向 _X 之後，在函式的類型中判斷下一個能顯示的值

```cpp
inline float nextafterf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Y*<br/>
浮點值。

### <a name="return-value"></a>傳回值

在函式的 _Y 中 _X 之後，傳回下一個顯示的值（在函數的類型中）

## <a name="phi"></a>phi

傳回引數的累計分佈函數

```cpp
inline float phi(float _X) restrict(amp);

inline double phi(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的累計分佈函數

## <a name="phif"></a>phif

傳回引數的累計分佈函數

```cpp
inline float phif(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的累計分佈函數

## <a name="pow"></a>  pow

計算 _X _Y 的乘冪

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);

inline double pow(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值，基底

*_Y*<br/>
浮點值、指數

### <a name="return-value"></a>傳回值

## <a name="powf"></a>powf

計算 _X _Y 的乘冪

```cpp
inline float powf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值，基底

*_Y*<br/>
浮點值、指數

### <a name="return-value"></a>傳回值

## <a name="probit"></a>probit

傳回引數的反向累計分佈函數

```cpp
inline float probit(float _X) restrict(amp);

inline double probit(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反向累計分佈函數

## <a name="probitf"></a>probitf

傳回引數的反向累計分佈函數

```cpp
inline float probitf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反向累計分佈函數

## <a name="rcbrt"></a>rcbrt

傳回引數的 cube 根項目的倒數

```cpp
inline float rcbrt(float _X) restrict(amp);

inline double rcbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的 cube 根項目的倒數

## <a name="rcbrtf"></a>rcbrtf

傳回引數的 cube 根項目的倒數

```cpp
inline float rcbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的 cube 根項目的倒數

## <a name="remainder"></a>數量

計算餘數： _X REM _Y

```cpp
inline float remainder(
    float _X,
    float _Y) restrict(amp);

inline double remainder(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Y*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 _X REM _Y

## <a name="remainderf"></a>remainderf

計算餘數： _X REM _Y

```cpp
inline float remainderf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Y*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 _X REM _Y

## <a name="remquo"></a>remquo

計算第一個指定引數除以第二個指定引數的餘數。 也會計算第一個指定引數之有效位數的商除以第二個指定引數的有效位數，並使用第三個引數中指定的位置傳回商。

```cpp
inline float remquo(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);

inline double remquo(
    double _X,
    double _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
第一個浮點引數。

*_Y*<br/>
第二個浮點引數。

*_Quo*<br/>
脫銷整數的位址，用來傳回 `_X` 的小數部分除以 `_Y`小數位的商。

### <a name="return-value"></a>傳回值

傳回 `_X` 除以 `_Y`的餘數。

## <a name="remquof"></a>remquof

計算第一個指定引數除以第二個指定引數的餘數。 也會計算第一個指定引數之有效位數的商除以第二個指定引數的有效位數，並使用第三個引數中指定的位置傳回商。

```cpp
inline float remquof(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
第一個浮點引數。

*_Y*<br/>
第二個浮點引數。

*_Quo*<br/>
脫銷整數的位址，用來傳回 `_X` 的小數部分除以 `_Y`小數位的商。

### <a name="return-value"></a>傳回值

傳回 `_X` 除以 `_Y`的餘數。

## <a name="round"></a>進行

將 _X 四捨五入到最接近的整數

```cpp
inline float round(float _X) restrict(amp);

inline double round(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回最接近的整數，_X

## <a name="roundf"></a>roundf

將 _X 四捨五入到最接近的整數

```cpp
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回最接近的整數，_X

## <a name="rsqrt"></a>rsqrt

傳回引數平方根的倒數

```cpp
inline float rsqrt(float _X) restrict(amp);

inline double rsqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數平方根的倒數

## <a name="rsqrtf"></a>rsqrtf

傳回引數平方根的倒數

```cpp
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數平方根的倒數

## <a name="scalb"></a>scalb

FLT_RADIX 乘冪 _Y，將 _X 相乘

```cpp
inline float scalb(
    float _X,
    float _Y) restrict(amp);

inline double scalb(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Y*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 _X \* （FLT_RADIX ^ _Y）

## <a name="scalbf"></a>scalbf

FLT_RADIX 乘冪 _Y，將 _X 相乘

```cpp
inline float scalbf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Y*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 _X \* （FLT_RADIX ^ _Y）

## <a name="scalbn"></a>scalbn

FLT_RADIX 乘冪 _Y，將 _X 相乘

```cpp
inline float scalbn(
    float _X,
    int _Y) restrict(amp);

inline double scalbn(
    double _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Y*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回 _X \* （FLT_RADIX ^ _Y）

## <a name="scalbnf"></a>scalbnf

FLT_RADIX 乘冪 _Y，將 _X 相乘

```cpp
inline float scalbnf(
    float _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Y*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回 _X \* （FLT_RADIX ^ _Y）

## <a name="signbit"></a>signbit

判斷 _X 的正負號是否為負數

```cpp
inline int signbit(float _X) restrict(amp);

inline int signbit(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

只有在 _X 的正負號為負數時，才會傳回非零值

## <a name="signbitf"></a>signbitf

判斷 _X 的正負號是否為負數

```cpp
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

只有在 _X 的正負號為負數時，才會傳回非零值

## <a name="sin"></a>  sin

計算引數的正弦值

```cpp
inline float sin(float _X) restrict(amp);

inline double sin(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的正弦值。

## <a name="sinf"></a>sinf

計算引數的正弦值

```cpp
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的正弦值。

## <a name="sincos"></a>sincos

計算 _X 的正弦和余弦值

```cpp
inline void sincos(
    float _X,
    _Out_ float* _S,
    _Out_ float* _C) restrict(amp);

inline void sincos(
    double _X,
    _Out_ double* _S,
    _Out_ double* _C) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_S*<br/>
傳回的正弦值 _X

*_C*<br/>
傳回的余弦值 _X

## <a name="sincosf"></a>sincosf

計算 _X 的正弦和余弦值

```cpp
inline void sincosf(
    float _X,
    _Out_ float* _S,
    _Out_ float* _C) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_S*<br/>
傳回的正弦值 _X

*_C*<br/>
傳回的余弦值 _X

## <a name="sinh"></a>  sinh

計算引數的雙曲正弦值

```cpp
inline float sinh(float _X) restrict(amp);

inline double sinh(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的雙曲正弦值

## <a name="sinhf"></a>sinhf

計算引數的雙曲正弦值

```cpp
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的雙曲正弦值

## <a name="sinpi"></a>sinpi

計算 pi \* 的正弦值 _X

```cpp
inline float sinpi(float _X) restrict(amp);

inline double sinpi(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 pi \* 的正弦值 _X

## <a name="sinpif"></a>sinpif

計算 pi \* 的正弦值 _X

```cpp
inline float sinpif(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 pi \* 的正弦值 _X

## <a name="sqrt"></a>  sqrt

計算引數的 squre 根

```cpp
inline float sqrt(float _X) restrict(amp);

inline double sqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的 squre 根目錄

## <a name="sqrtf"></a>sqrtf

計算引數的 squre 根

```cpp
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的 squre 根目錄

## <a name="tan"></a>  tan

計算引數的正切值

```cpp
inline float tan(float _X) restrict(amp);

inline double tan(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的正切值

## <a name="tanf"></a>tanf

計算引數的正切值

```cpp
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的正切值

## <a name="tanh"></a>  tanh

計算引數的雙曲正切值

```cpp
inline float tanh(float _X) restrict(amp);

inline double tanh(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的雙曲正切值。

## <a name="tanhf"></a>tanhf

計算引數的雙曲正切值

```cpp
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的雙曲正切值。

## <a name="tanpi"></a>tanpi

計算 pi \* 的正切值 _X

```cpp
inline float tanpi(float _X) restrict(amp);

inline double tanpi(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 pi \* 的正切值 _X

## <a name="tanpif"></a>tanpif

計算 pi \* 的正切值 _X

```cpp
inline float tanpif(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 pi \* 的正切值 _X

## <a name="tgamma"></a>tgamma

計算的 gamma 函數 _X

```cpp
inline float tgamma(float _X) restrict(amp);

inline double tgamma(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 gamma 函數的結果 _X

## <a name="tgammaf"></a>tgammaf

計算的 gamma 函數 _X

```cpp
inline float tgammaf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 gamma 函數的結果 _X

## <a name="trunc"></a>trunc

截斷整陣列件的引數

```cpp
inline float trunc(float _X) restrict(amp);

inline double trunc(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的整陣列件

## <a name="truncf"></a>truncf

截斷整陣列件的引數

```cpp
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的整陣列件

## <a name="see-also"></a>另請參閱

[Concurrency::precise_math 命名空間](concurrency-precise-math-namespace.md)
