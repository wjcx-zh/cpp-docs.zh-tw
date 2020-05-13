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
ms.openlocfilehash: ee6ab2313fbdc288ebba1b3fdacf192b7b578eb6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321863"
---
# <a name="concurrencyprecise_math-namespace-functions"></a>Concurrency::precise_math 命名空間函式

||||
|-|-|-|
|[阿科斯](#acos)|[acosf](#acosf)|[acosh](#acosh)|
|[acoshf](#acoshf)|[阿辛](#asin)|[asinf](#asinf)|
|[asinh](#asinh)|[asinhf](#asinhf)|[阿坦](#atan)|
|[阿坦2](#atan2)|[atan2f](#atan2f)|[atanf](#atanf)|
|[atanh](#atanh)|[atanhf](#atanhf)|[cbrt](#cbrt)|
|[cbrtf](#cbrtf)|[塞伊爾](#ceil)|[ceilf](#ceilf)|
|[複製符號](#copysign)|[copysignf](#copysignf)|[因為](#cos)|
|[cosf](#cosf)|[cosh](#cosh)|[coshf](#coshf)|
|[科斯皮](#cospi)|[科斯皮夫](#cospif)|[erf](#erf)|
|[erfc](#erfc)|[erfcf](#erfcf)|[埃爾夫夫夫](#erfcinv)|
|[埃爾夫辛夫夫](#erfcinvf)|[erff](#erff)|[埃爾菲夫](#erfinv)|
|[埃爾芬夫夫](#erfinvf)|[exp](#exp)|[exp10](#exp10)|
|[exp10f](#exp10f)|[exp2](#exp2)|[exp2f](#exp2f)|
|[expf](#expf)|[expm1](#expm1)|[expm1f](#expm1f)|
|[fabs](#fabs)|[fabsf](#fabsf)|[地板](#floor)|
|[fdim](#fdim)|[fdimf](#fdimf)||
|[floorf](#floorf)|[fma](#fma)|[fmaf](#fmaf)|
[fmax](#fmax)|[fmaxf](#fmaxf)||
|[fmin](#fmin)|[fminf](#fminf)|[fmod](#fmod)|
|[fmodf](#fmodf)|[fpclassify](#fpclassify)|[frexp](#frexp)|
|[弗雷克斯普夫](#frexpf)|[假說](#hypot)|[hypotf](#hypotf)|
|[ilogb](#ilogb)|[ilogbf](#ilogbf)|[是有限的](#isfinite)|
|[是因夫](#isinf)|[isnan](#isnan)|[isnormal](#isnormal)|
|[ldexp](#ldexp)|[爾德克斯普夫](#ldexpf)|[lgamma](#lgamma)|
|[lgammaf](#lgammaf)|[紀錄](#log)|[紀錄10](#log10)|
|[log10f](#log10f)|[log1p](#log1p)|[log1pf](#log1pf)|
|[紀錄2](#log2)|[log2f](#log2f)|[logb](#logb)|
|[logbf](#logbf)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[nan](#nan)|[nanf](#nanf)|
|[nearbyint](#nearbyint)|[nearbyintf](#nearbyintf)|[nextafter](#nextafter)|
|[下一個後](#nextafterf)|[披](#phi)|[菲夫](#phif)|
|[pow](#pow)|[powf](#powf)|[普羅比特](#probit)|
|[probitf](#probitf)|[rcbrt](#rcbrt)|[rcbrtf](#rcbrtf)|
|[remainder](#remainder)|[remainderf](#remainderf)|[remquo](#remquo)|
|[remquof](#remquof)|[輪](#round)|[roundf](#roundf)|
|[rsqrt](#rsqrt)|[rsqrtf](#rsqrtf)|[鱗狀](#scalb)|
|[卡爾布布](#scalbf)|[scalbn](#scalbn)|[scalbnf](#scalbnf)|
|[signbit](#signbit)|[符號比夫](#signbitf)|[罪](#sin)|
|[辛科斯](#sincos)|[辛科斯夫](#sincosf)|[sinf](#sinf)|
|[sinh](#sinh)|[sinhf](#sinhf)|[辛皮](#sinpi)|
|[辛菲夫](#sinpif)|[sqrt](#sqrt)|[sqrtf](#sqrtf)|
|[潭](#tan)|[tanf](#tanf)|[坦赫](#tanh)|
|[tanhf](#tanhf)|[坦皮](#tanpi)|[坦菲夫](#tanpif)|
|[tgamma](#tgamma)|[tgammaf](#tgammaf)|[特魯恩](#trunc)|
|[truncf](#truncf)|

## <a name="acos"></a><a name="acos"></a>阿科斯

計算參數的弧形

```cpp
inline float acos(float _X) restrict(amp);

inline double acos(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的弧形值

## <a name="acosf"></a><a name="acosf"></a>阿科斯夫

計算參數的弧形

```cpp
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的弧形值

## <a name="acosh"></a><a name="acosh"></a>阿科什

計算參數的反向雙曲結果

```cpp
inline float acosh(float _X) restrict(amp);

inline double acosh(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的反向雙曲元值

## <a name="acoshf"></a><a name="acoshf"></a>阿科什夫

計算參數的反向雙曲結果

```cpp
inline float acoshf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的反向雙曲元值

## <a name="asin"></a><a name="asin"></a>阿辛

計算參數的弧形

```cpp
inline float asin(float _X) restrict(amp);

inline double asin(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的弧形值

## <a name="asinf"></a><a name="asinf"></a>阿辛夫

計算參數的弧形

```cpp
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的弧形值

## <a name="asinh"></a><a name="asinh"></a>阿辛

計算參數的反向雙曲正則

```cpp
inline float asinh(float _X) restrict(amp);

inline double asinh(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的反向雙曲正則值

## <a name="asinhf"></a><a name="asinhf"></a>阿辛夫

計算參數的反向雙曲正則

```cpp
inline float asinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的反向雙曲正則值

## <a name="atan"></a><a name="atan"></a>阿坦

計算引數的反正切

```cpp
inline float atan(float _X) restrict(amp);

inline double atan(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的弧形值

## <a name="atan2"></a><a name="atan2"></a>阿坦2

計算_Y/_X的弧形

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

返回_Y/_X的弧線值

## <a name="atan2f"></a><a name="atan2f"></a>阿坦2f

計算_Y/_X的弧形

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

返回_Y/_X的弧線值

## <a name="atanf"></a><a name="atanf"></a>阿坦夫

計算引數的反正切

```cpp
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的弧形值

## <a name="atanh"></a><a name="atanh"></a>阿坦

計算參數的反向雙曲切線

```cpp
inline float atanh(float _X) restrict(amp);

inline double atanh(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的反向雙曲線切線值

## <a name="atanhf"></a><a name="atanhf"></a>阿坦hf

計算參數的反向雙曲切線

```cpp
inline float atanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的反向雙曲線切線值

## <a name="cbrt"></a><a name="cbrt"></a>cbrt

計算參數的實際多維資料集根

```cpp
inline float cbrt(float _X) restrict(amp);

inline double cbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的實際多維資料集根

## <a name="cbrtf"></a><a name="cbrtf"></a>cbrtf

計算參數的實際多維資料集根

```cpp
inline float cbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的實際多維資料集根

## <a name="ceil"></a><a name="ceil"></a>塞伊爾

計算參數的上限

```cpp
inline float ceil(float _X) restrict(amp);

inline double ceil(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的上限

## <a name="ceilf"></a><a name="ceilf"></a>切爾夫

計算參數的上限

```cpp
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的上限

## <a name="copysign"></a><a name="copysign"></a>複製符號

產生具有_X量和_Y標誌的值

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

傳回具有_X量和_Y旗標的值

## <a name="copysignf"></a><a name="copysignf"></a>複製符號f

產生具有_X量和_Y標誌的值

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

傳回具有_X量和_Y旗標的值

## <a name="cos"></a><a name="cos"></a>因為

計算引數的餘弦

```cpp
inline float cos(float _X) restrict(amp);

inline double cos(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的可數值

## <a name="cosf"></a><a name="cosf"></a>科斯夫

計算引數的餘弦

```cpp
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的可數值

## <a name="cosh"></a><a name="cosh"></a>科什

計算參數的雙曲性拋物值

```cpp
inline float cosh(float _X) restrict(amp);

inline double cosh(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的雙曲性拋物值

## <a name="coshf"></a><a name="coshf"></a>科斯夫

計算參數的雙曲性拋物值

```cpp
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的雙曲性拋物值

## <a name="cospi"></a><a name="cospi"></a>科斯皮

計算\*pi _X 的可數值

```cpp
inline float cospi(float _X) restrict(amp);

inline double cospi(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回\*pi _X的可數值

## <a name="cospif"></a><a name="cospif"></a>科斯皮夫

計算\*pi _X 的可數值

```cpp
inline float cospif(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回\*pi _X的可數值

## <a name="erf"></a><a name="erf"></a>埃爾夫

計算_X的錯誤函數

```cpp
inline float erf(float _X) restrict(amp);

inline double erf(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回_X的錯誤函數

## <a name="erfc"></a><a name="erfc"></a>埃爾夫克

計算_X的互補誤差函數

```cpp
inline float erfc(float _X) restrict(amp);

inline double erfc(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回_X的互補誤差函數

## <a name="erfcf"></a><a name="erfcf"></a>埃爾夫夫

計算_X的互補誤差函數

```cpp
inline float erfcf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回_X的互補誤差函數

## <a name="erfcinv"></a><a name="erfcinv"></a>埃爾夫夫夫

計算_X的反向互補誤差函數

```cpp
inline float erfcinv(float _X) restrict(amp);

inline double erfcinv(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

返回_X的反向互補誤差函數

## <a name="erfcinvf"></a><a name="erfcinvf"></a>埃爾夫辛夫夫

計算_X的反向互補誤差函數

```cpp
inline float erfcinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

返回_X的反向互補誤差函數

## <a name="erff"></a><a name="erff"></a>埃爾夫

計算_X的錯誤函數

```cpp
inline float erff(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回_X的錯誤函數

## <a name="erfinv"></a><a name="erfinv"></a>埃爾菲夫

計算_X的逆誤差函數

```cpp
inline float erfinv(float _X) restrict(amp);

inline double erfinv(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

返回_X的反向誤差函數

## <a name="erfinvf"></a><a name="erfinvf"></a>埃爾芬夫夫

計算_X的逆誤差函數

```cpp
inline float erfinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

返回_X的反向誤差函數

## <a name="exp10"></a><a name="exp10"></a>exp10

計算參數的基-10 指數

```cpp
inline float exp10(float _X) restrict(amp);

inline double exp10(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的基-10 指數

## <a name="exp10f"></a><a name="exp10f"></a>exp10f

計算參數的基-10 指數

```cpp
inline float exp10f(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的基-10 指數

## <a name="expm1"></a><a name="expm1"></a>expm1

計算引數以 e 為底數的指數，減 1。

```cpp
inline float expm1(float exponent) restrict(amp);

inline double expm1(double exponent) restrict(amp);
```

### <a name="parameters"></a>參數

*指數*<br/>
數學運算`e`<sup>式 n</sup>的指數項`e`*n,* 其中 是自然對數的基點。

### <a name="return-value"></a>傳回值

傳回引數以 e 為底數的指數，減 1。

## <a name="expm1f"></a><a name="expm1f"></a>expm1f

計算引數以 e 為底數的指數，減 1。

```cpp
inline float expm1f(float exponent) restrict(amp);
```

### <a name="parameters"></a>參數

*指數*<br/>
數學運算`e`<sup>式 n</sup>的指數項`e`*n,* 其中 是自然對數的基點。

### <a name="return-value"></a>傳回值

傳回引數以 e 為底數的指數，減 1。

## <a name="exp"></a><a name="exp"></a>exp

計算參數的基-e 指數

```cpp
inline float exp(float _X) restrict(amp);

inline double exp(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的基-e 指數

## <a name="expf"></a><a name="expf"></a>expf

計算參數的基-e 指數

```cpp
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的基-e 指數

## <a name="exp2"></a><a name="exp2"></a>exp2

計算參數的基-2 指數

```cpp
inline float exp2(float _X) restrict(amp);

inline double exp2(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的基底 2 指數

## <a name="exp2f"></a><a name="exp2f"></a>exp2f

計算參數的基-2 指數

```cpp
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的基底 2 指數

## <a name="fabs"></a><a name="fabs"></a>晶圓廠

傳回參數的絕對值

```cpp
inline float fabs(float _X) restrict(amp);

inline double fabs(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的絕對值

## <a name="fabsf"></a><a name="fabsf"></a>法布斯夫

傳回參數的絕對值

```cpp
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的絕對值

## <a name="fdim"></a><a name="fdim"></a>外國直接投資姆

計算參數之間的正差。

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

如果_X大於_Y,則_X和_Y之間的差異;否則,|0。

## <a name="fdimf"></a><a name="fdimf"></a>盧夫菲夫

計算參數之間的正差。

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

如果_X大於_Y,則_X和_Y之間的差異;否則,|0。

## <a name="floor"></a><a name="floor"></a>地板

計算參數的層級

```cpp
inline float floor(float _X) restrict(amp);

inline double floor(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的層級

## <a name="floorf"></a><a name="floorf"></a>地板

計算參數的層級

```cpp
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的層級

## <a name="a-namefma-fma"></a><a name="fma">fma

計算第一個和第二個指定參數的組成,然後將第三個指定的參數添加到結果;整個計算作為單個操作執行。

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
第一個浮點參數。
*_Y*<br/>
第二個浮點參數。
*_Z*<br/>
第三個浮點參數。

### <a name="return-value"></a>傳回值

運算式(_X_Y) \* = _Z的結果。 整個計算作為單個操作執行;也就是說,子表達式計算為無限精度,並且只有最終結果四捨五入。

## <a name="fmaf"></a><a name="fmaf"></a>費夫

計算第一個和第二個指定參數的組成,然後將第三個指定的參數添加到結果;整個計算作為單個操作執行。

```cpp
inline float fmaf(
   float _X,
   float _Y,
   float _Z
) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
第一個浮點參數。
*_Y*<br/>
第二個浮點參數。
*_Z*<br/>
第三個浮點參數。

### <a name="return-value"></a>傳回值

運算式(_X_Y) \* = _Z的結果。 整個計算作為單個操作執行;也就是說,子表達式計算為無限精度,並且只有最終結果四捨五入。

## <a name="fmax"></a><a name="fmax"></a>fmax

確定參數的最大數值

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

傳回參數的最大數值

## <a name="fmaxf"></a><a name="fmaxf"></a>fmaxf

確定參數的最大數值

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

傳回參數的最大數值

## <a name="fmin"></a><a name="fmin"></a>fmin

確定參數的最小數值

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

傳回參數的最小數值

## <a name="fminf"></a><a name="fminf"></a>fminf

確定參數的最小數值

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

傳回參數的最小數值

## <a name="fmod-function-c-amp"></a><a name="fmod"></a>fmod 功能(C++ AMP)

計算第一個指定參數的其餘部分除以第二個指定參數。

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
第一個浮點參數。

*_Y*<br/>
第二個浮點參數。

### <a name="return-value"></a>傳回值

其餘除`_X``_Y`以 :`_X``_X` - `_Y`*n*`_Y`*n**n*即 n 的值, 其中 n 是整體整數,因此 n 的幅度小於的幅度。  -  `_Y`

## <a name="fmodf"></a><a name="fmodf"></a>fmodf

計算第一個指定參數的其餘部分除以第二個指定參數。

```cpp
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
第一個浮點參數。

*_Y*<br/>
第二個浮點參數。

### <a name="return-value"></a>傳回值

其餘除`_X``_Y`以 :`_X``_X` - `_Y`*n*`_Y`*n**n*即 n 的值, 其中 n 是整體整數,因此 n 的幅度小於的幅度。  -  `_Y`

## <a name="fpclassify"></a><a name="fpclassify"></a>fp分類

將參數值類別為 NaN、無限、正常、次正態、零

```cpp
inline int fpclassify(float _X) restrict(amp);

inline int fpclassify(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

返回與參數的值相適應的編號分類宏的值。

## <a name="frexp"></a><a name="frexp"></a>弗雷費浦

取得_X的曼蒂薩和指數

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
在浮點值中傳回 _X的整數指數

### <a name="return-value"></a>傳回值

返回曼蒂薩_X

## <a name="frexpf"></a><a name="frexpf"></a>弗雷克斯普夫

取得_X的曼蒂薩和指數

```cpp
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Exp*<br/>
在浮點值中傳回 _X的整數指數

### <a name="return-value"></a>傳回值

返回曼蒂薩_X

## <a name="hypot"></a><a name="hypot"></a>假說

計算_X和_Y平方和的平方根

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

返回_X和_Y的平方和的平方根

## <a name="hypotf"></a><a name="hypotf"></a>hypotf

計算_X和_Y平方和的平方根

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

返回_X和_Y的平方和的平方根

## <a name="ilogb"></a><a name="ilogb"></a>伊洛格布

擷取_X的指數作為簽名的 int 值

```cpp
inline int ilogb(float _X) restrict(amp);

inline int ilogb(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

將_X的指數作為已簽名的 int 值傳回

## <a name="ilogbf"></a><a name="ilogbf"></a>伊洛格布布

擷取_X的指數作為簽名的 int 值

```cpp
inline int ilogbf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

將_X的指數作為已簽名的 int 值傳回

## <a name="isfinite"></a><a name="isfinite"></a>是有限的

確定參數是否具有有限值

```cpp
inline int isfinite(float _X) restrict(amp);

inline int isfinite(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

僅當參數具有有限值時,才返回非零值

## <a name="isinf"></a><a name="isinf"></a>是因夫

確定參數是否為無窮大

```cpp
inline int isinf(float _X) restrict(amp);

inline int isinf(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

僅當 參數具有無窮值時,才返回非零值

## <a name="isnan"></a><a name="isnan"></a>isnan

確定參數是否為 NaN

```cpp
inline int isnan(float _X) restrict(amp);

inline int isnan(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

僅當參數具有 NaN 值時,才傳回非零值

## <a name="isnormal"></a><a name="isnormal"></a>是正常現象

確定參數是否為正常參數

```cpp
inline int isnormal(float _X) restrict(amp);

inline int isnormal(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

僅當 參數具有正常值時,才傳回非零值

## <a name="ldexp"></a><a name="ldexp"></a>爾德莫

從指定的指數和指數計算實數。

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
浮點值,曼蒂薩

*_Exp*<br/>
整數值,指數

### <a name="return-value"></a>傳回值

返回_X \* 2+_Exp

## <a name="ldexpf"></a><a name="ldexpf"></a>爾德克斯普夫

從指定的指數和指數計算實數。

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值,曼蒂薩

*_Exp*<br/>
整數值,指數

### <a name="return-value"></a>傳回值

返回_X \* 2+_Exp

## <a name="lgamma"></a><a name="lgamma"></a>盧馬馬

計算參數伽馬絕對值的自然對數

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
返回符號

### <a name="return-value"></a>傳回值

傳回參數的伽馬絕對值的自然對數

## <a name="lgammaf"></a><a name="lgammaf"></a>盧加馬夫

計算參數伽馬絕對值的自然對數

```cpp
inline float lgammaf(
    float _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Sign*<br/>
返回符號

### <a name="return-value"></a>傳回值

傳回參數的伽馬絕對值的自然對數

## <a name="log"></a><a name="log"></a>紀錄

計算參數的基數-e對數

```cpp
inline float log(float _X) restrict(amp);

inline double log(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的基-e對數

## <a name="log10"></a><a name="log10"></a>紀錄10

計算參數的基數-10對數

```cpp
inline float log10(float _X) restrict(amp);

inline double log10(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的基 10 對數

## <a name="log10f"></a><a name="log10f"></a>記錄10f

計算參數的基數-10對數

```cpp
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的基 10 對數

## <a name="log1p"></a><a name="log1p"></a>紀錄1p

計算 1 的基數-e 對數加上參數

```cpp
inline float log1p(float _X) restrict(amp);

inline double log1p(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 1 的基-e 對數加上參數

## <a name="log1pf"></a><a name="log1pf"></a>紀錄1pf

計算 1 的基數-e 對數加上參數

```cpp
inline float log1pf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 1 的基-e 對數加上參數

## <a name="log2"></a><a name="log2"></a>紀錄2

計算參數的基 2 對數

```cpp
inline float log2(float _X) restrict(amp);

inline double log2(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的基 10 對數

## <a name="log2f"></a><a name="log2f"></a>紀錄2f

計算參數的基 2 對數

```cpp
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的基 10 對數

## <a name="logb"></a><a name="logb"></a>紀錄

提取_X的指數,作為浮點格式的簽名整數值

```cpp
inline float logb(float _X) restrict(amp);

inline double logb(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回已簽署的_X指數

## <a name="logbf"></a><a name="logbf"></a>logbf

提取_X的指數,作為浮點格式的簽名整數值

```cpp
inline float logbf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回已簽署的_X指數

## <a name="logf"></a><a name="logf"></a>logf

計算參數的基數-e對數

```cpp
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的基-e對數

## <a name="modf"></a><a name="modf"></a>modf

將指定的參數拆分為小數和整數部分。

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
[出]的整數部分`_X`作為浮點值。

### <a name="return-value"></a>傳回值

的符號小數部份`_X`。

## <a name="modff"></a><a name="modff"></a>莫德夫

將指定的參數拆分為小數和整數部分。

```cpp
inline float modff(
    float _X,
    _Out_ float* _Iptr) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Iptr*<br/>
的整數部分`_X`作為浮點值。

### <a name="return-value"></a>傳回值

返回`_X`的已簽名小數部分。

## <a name="nan"></a><a name="nan"></a>南

傳回安靜的 NaN

```cpp
inline double nan(int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回一個安靜的 NaN(如果可用),內容以_X

## <a name="nanf"></a><a name="nanf"></a>南夫

傳回安靜的 NaN

```cpp
inline float nanf(int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回一個安靜的 NaN(如果可用),內容以_X

## <a name="nearbyint"></a><a name="nearbyint"></a>附近

使用當前舍入方向將參數舍入到浮點格式的整數值。

```cpp
inline float nearbyint(float _X) restrict(amp);

inline double nearbyint(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

返回舍入的整數值。

## <a name="nearbyintf"></a><a name="nearbyintf"></a>附近

使用當前舍入方向將參數舍入到浮點格式的整數值。

```cpp
inline float nearbyintf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

返回舍入的整數值。

## <a name="nextafter"></a><a name="nextafter"></a>之後

在_X後,確定函數類型的下一個可表示值_Y

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

傳回函數型態中的下一個可表示值,_X_Y

## <a name="nextafterf"></a><a name="nextafterf"></a>下一個後

在_X後,確定函數類型的下一個可表示值_Y

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

傳回函數型態中的下一個可表示值,_X_Y

## <a name="phi"></a><a name="phi"></a>披

傳回參數的累積分配函數

```cpp
inline float phi(float _X) restrict(amp);

inline double phi(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的累積分配函數

## <a name="phif"></a><a name="phif"></a>菲夫

傳回參數的累積分配函數

```cpp
inline float phif(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的累積分配函數

## <a name="pow"></a><a name="pow"></a>戰俘

計算_X提升到_Y功率

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
浮點值,基

*_Y*<br/>
浮點值,指數

### <a name="return-value"></a>傳回值

## <a name="powf"></a><a name="powf"></a>波夫

計算_X提升到_Y功率

```cpp
inline float powf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值,基

*_Y*<br/>
浮點值,指數

### <a name="return-value"></a>傳回值

## <a name="probit"></a><a name="probit"></a>普羅比特

傳回參數的反向累積分配函數

```cpp
inline float probit(float _X) restrict(amp);

inline double probit(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的反向累積分配函數

## <a name="probitf"></a><a name="probitf"></a>probitf

傳回參數的反向累積分配函數

```cpp
inline float probitf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的反向累積分配函數

## <a name="rcbrt"></a><a name="rcbrt"></a>rcbrt

傳回參數的多資料集根的對等

```cpp
inline float rcbrt(float _X) restrict(amp);

inline double rcbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的多資料集根的對等

## <a name="rcbrtf"></a><a name="rcbrtf"></a>rcbrtf

傳回參數的多資料集根的對等

```cpp
inline float rcbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的多資料集根的對等

## <a name="remainder"></a><a name="remainder"></a>剩餘

計算剩餘部份:_X REM _Y

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

## <a name="remainderf"></a><a name="remainderf"></a>余夫

計算剩餘部份:_X REM _Y

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

## <a name="remquo"></a><a name="remquo"></a>雷姆庫

計算第一個指定參數的其餘部分除以第二個指定參數。 還計算第一個指定參數的符號的商,除以第二個指定參數的符號,並使用第三個參數中指定的位置返回商。

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
第一個浮點參數。

*_Y*<br/>
第二個浮點參數。

*_Quo*<br/>
[出]傳回`_X`接收的數字, 以的小數字的數字的數字的位址`_Y`。

### <a name="return-value"></a>傳回值

傳回除`_X`以的剩餘`_Y`部份 。

## <a name="remquof"></a><a name="remquof"></a>雷姆庫烏姆

計算第一個指定參數的其餘部分除以第二個指定參數。 還計算第一個指定參數的符號的商,除以第二個指定參數的符號,並使用第三個參數中指定的位置返回商。

```cpp
inline float remquof(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
第一個浮點參數。

*_Y*<br/>
第二個浮點參數。

*_Quo*<br/>
[出]傳回`_X`接收的數字, 以的小數字的數字的數字的位址`_Y`。

### <a name="return-value"></a>傳回值

傳回除`_X`以的剩餘`_Y`部份 。

## <a name="round"></a><a name="round"></a>輪

舍_X到最接近的整數

```cpp
inline float round(float _X) restrict(amp);

inline double round(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

返回最接近的_X整數

## <a name="roundf"></a><a name="roundf"></a>圓夫

舍_X到最接近的整數

```cpp
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

返回最接近的_X整數

## <a name="rsqrt"></a><a name="rsqrt"></a>rsqrt

傳回參數的平方根的對等項目

```cpp
inline float rsqrt(float _X) restrict(amp);

inline double rsqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的平方根的對等項目

## <a name="rsqrtf"></a><a name="rsqrtf"></a>rsqrtf

傳回參數的平方根的對等項目

```cpp
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的平方根的對等項目

## <a name="scalb"></a><a name="scalb"></a>鱗狀

將_X乘以FLT_RADIX到功率_Y

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

返回_X(FLT_RADIX \* = _Y)

## <a name="scalbf"></a><a name="scalbf"></a>卡爾布布

將_X乘以FLT_RADIX到功率_Y

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

返回_X(FLT_RADIX \* = _Y)

## <a name="scalbn"></a><a name="scalbn"></a>斯萬布

將_X乘以FLT_RADIX到功率_Y

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

返回_X(FLT_RADIX \* = _Y)

## <a name="scalbnf"></a><a name="scalbnf"></a>卡爾本夫

將_X乘以FLT_RADIX到功率_Y

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

返回_X(FLT_RADIX \* = _Y)

## <a name="signbit"></a><a name="signbit"></a>符號位

確定_X的符號是否為負

```cpp
inline int signbit(float _X) restrict(amp);

inline int signbit(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

僅當 _X 符號為負數時,才會返回非零值

## <a name="signbitf"></a><a name="signbitf"></a>符號比夫

確定_X的符號是否為負

```cpp
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

僅當 _X 符號為負數時,才會返回非零值

## <a name="sin"></a><a name="sin"></a>罪

計算參數的子值

```cpp
inline float sin(float _X) restrict(amp);

inline double sin(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的子值

## <a name="sinf"></a><a name="sinf"></a>辛夫

計算參數的子值

```cpp
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的子值

## <a name="sincos"></a><a name="sincos"></a>辛科斯

計算_X的子值與可次值

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
傳回_X子值

*_C*<br/>
傳回_X的可數值

## <a name="sincosf"></a><a name="sincosf"></a>辛科斯夫

計算_X的子值與可次值

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
傳回_X子值

*_C*<br/>
傳回_X的可數值

## <a name="sinh"></a><a name="sinh"></a>辛赫

計算參數的雙曲子值

```cpp
inline float sinh(float _X) restrict(amp);

inline double sinh(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的雙曲子值

## <a name="sinhf"></a><a name="sinhf"></a>辛夫

計算參數的雙曲子值

```cpp
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的雙曲子值

## <a name="sinpi"></a><a name="sinpi"></a>辛皮

計算\*pi _X的子值

```cpp
inline float sinpi(float _X) restrict(amp);

inline double sinpi(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回\*pi _X的子值

## <a name="sinpif"></a><a name="sinpif"></a>辛菲夫

計算\*pi _X的子值

```cpp
inline float sinpif(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回\*pi _X的子值

## <a name="sqrt"></a><a name="sqrt"></a>sqrt

計算參數的 squre 根

```cpp
inline float sqrt(float _X) restrict(amp);

inline double sqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的 squre 根

## <a name="sqrtf"></a><a name="sqrtf"></a>斯克爾夫

計算參數的 squre 根

```cpp
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的 squre 根

## <a name="tan"></a><a name="tan"></a>潭

計算參數的切線值

```cpp
inline float tan(float _X) restrict(amp);

inline double tan(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的切線值

## <a name="tanf"></a><a name="tanf"></a>坦夫

計算參數的切線值

```cpp
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的切線值

## <a name="tanh"></a><a name="tanh"></a>坦赫

計算參數的雙曲切線值

```cpp
inline float tanh(float _X) restrict(amp);

inline double tanh(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的雙曲切線值

## <a name="tanhf"></a><a name="tanhf"></a>坦夫

計算參數的雙曲切線值

```cpp
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的雙曲切線值

## <a name="tanpi"></a><a name="tanpi"></a>坦皮

計算\*pi 的切線值_X

```cpp
inline float tanpi(float _X) restrict(amp);

inline double tanpi(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回\*pi 的切線值_X

## <a name="tanpif"></a><a name="tanpif"></a>坦菲夫

計算\*pi 的切線值_X

```cpp
inline float tanpif(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回\*pi 的切線值_X

## <a name="tgamma"></a><a name="tgamma"></a>特伽馬

計算_X的伽瑪函數

```cpp
inline float tgamma(float _X) restrict(amp);

inline double tgamma(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

返回_X伽瑪函數的結果

## <a name="tgammaf"></a><a name="tgammaf"></a>特加馬夫

計算_X的伽瑪函數

```cpp
inline float tgammaf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

返回_X伽瑪函數的結果

## <a name="trunc"></a><a name="trunc"></a>特魯恩

將參數截斷到整陣元件

```cpp
inline float trunc(float _X) restrict(amp);

inline double trunc(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的整數元件

## <a name="truncf"></a><a name="truncf"></a>特倫CF

將參數截斷到整陣元件

```cpp
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的整數元件

## <a name="see-also"></a>另請參閱

[併發性::p重新調整名稱空間](concurrency-precise-math-namespace.md)
