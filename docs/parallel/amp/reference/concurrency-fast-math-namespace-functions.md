---
title: Concurrency::fast_math 命名空間函式
ms.date: 11/04/2016
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
ms.assetid: f5763d62-795b-4de6-a7a5-c7115f158708
ms.openlocfilehash: ff919016449723ad67e029a249ec222ccf1fe6a4
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831056"
---
# <a name="concurrencyfast_math-namespace-functions"></a>Concurrency::fast_math 命名空間函式

:::row:::
   :::column span="":::
      [`acos`](#acos)\
      [`acosf`](#acosf)\
      [`asin`](#asin)\
      [`asinf`](#asinf)\
      [`atan`](#atan)\
      [`atan2`](#atan2)\
      [`atan2f`](#atan2f)\
      [`atanf`](#atanf)\
      [`ceil`](#ceil)\
      [`ceilf`](#ceilf)\
      [`cos`](#cos)\
      [`cosf`](#cosf)\
      [`cosh`](#cosh)\
      [`coshf`](#coshf)\
      [`exp`](#exp)\
      [`exp2`](#exp2)\
      [`exp2f`](#exp2f)
   :::column-end:::
   :::column span="":::
      [`expf`](#expf)\
      [`fabs`](#fabs)\
      [`fabsf`](#fabsf)\
      [`floor`](#floor)\
      [`floorf`](#floorf)\
      [`fmax`](#fmax)\
      [`fmaxf`](#fmaxf)\
      [`fmin`](#fmin)\
      [`fminf`](#fminf)\
      [`fmod`](#fmod)\
      [`fmodf`](#fmodf)\
      [`frexp`](#frexp)\
      [`frexpf`](#frexpf)\
      [`isfinite`](#isfinite)\
      [`isinf`](#isinf)\
      [`isnan`](#isnan)
   :::column-end:::
   :::column span="":::
      [`ldexp`](#ldexp)\
      [`ldexpf`](#ldexpf)\
      [`log`](#log)\
      [`log10`](#log10)\
      [`log10f`](#log10f)\
      [`log2`](#log2)\
      [`log2f`](#log2f)\
      [`logf`](#logf)\
      [`modf`](#modf)\
      [`modff`](#modff)\
      [`pow`](#pow)\
      [`powf`](#powf)\
      [`round`](#round)\
      [`roundf`](#roundf)\
      [`rsqrt`](#rsqrt)\
      [`rsqrtf`](#rsqrtf)
   :::column-end:::
   :::column span="":::
      [`signbit`](#signbit)\
      [`signbitf`](#signbitf)\
      [`sin`](#sin)\
      [`sincos`](#sincos)\
      [`sincosf`](#sincosf)\
      [`sinf`](#sinf)\
      [`sinh`](#sinh)\
      [`sinhf`](#sinhf)\
      [`sqrt`](#sqrt)\
      [`sqrtf`](#sqrtf)\
      [`tan`](#tan)\
      [`tanf`](#tanf)\
      [`tanh`](#tanh)\
      [`tanhf`](#tanhf)\
      [`trunc`](#trunc)\
      [`truncf`](#truncf)
   :::column-end:::
:::row-end:::

## <a name="acos"></a><a name="acos"></a> acos

計算引數的反余弦

```cpp
inline float acos(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反余弦值。

## <a name="acosf"></a><a name="acosf"></a> acosf

計算引數的反余弦

```cpp
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反余弦值。

## <a name="asin"></a><a name="asin"></a> asin

計算引數的反正弦

```cpp
inline float asin(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反正弦值。

## <a name="asinf"></a><a name="asinf"></a> asinf

計算引數的反正弦

```cpp
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反正弦值。

## <a name="atan"></a><a name="atan"></a> atan

計算引數的反正切

```cpp
inline float atan(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反正切值。

## <a name="atan2"></a><a name="atan2"></a> atan2

計算 _Y/_X 的反正切值

```cpp
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

傳回 _Y/_X 的反正切值。

## <a name="atan2f"></a><a name="atan2f"></a> atan2f

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

傳回 _Y/_X 的反正切值。

## <a name="atanf"></a><a name="atanf"></a> atanf

計算引數的反正切

```cpp
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的反正切值。

## <a name="ceil"></a><a name="ceil"></a> ceil

計算引數的上限

```cpp
inline float ceil(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的上限

## <a name="ceilf"></a><a name="ceilf"></a> ceilf

計算引數的上限

```cpp
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的上限

## <a name="cosf"></a><a name="cosf"></a> cosf

計算引數的餘弦

```cpp
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的余弦值

## <a name="coshf"></a><a name="coshf"></a> coshf

計算引數的雙曲余弦值

```cpp
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的雙曲余弦值

## <a name="cos"></a><a name="cos"></a> 因為

計算引數的餘弦

```cpp
inline float cos(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的余弦值

## <a name="cosh"></a><a name="cosh"></a> cosh

計算引數的雙曲余弦值

```cpp
inline float cosh(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的雙曲余弦值

## <a name="exp"></a><a name="exp"></a> exp

計算引數的底數-e 指數

```cpp
inline float exp(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的底數-e 指數

## <a name="exp2"></a><a name="exp2"></a> exp2

計算引數的以2為底數的指數

```cpp
inline float exp2(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的基底 2 指數

## <a name="exp2f"></a><a name="exp2f"></a> exp2f

計算引數的以2為底數的指數

```cpp
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的基底 2 指數

## <a name="expf"></a><a name="expf"></a> expf

計算引數的底數-e 指數

```cpp
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的底數-e 指數

## <a name="fabs"></a><a name="fabs"></a> fabs

傳回引數的絕對值。

```cpp
inline float fabs(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回引數的絕對值。

## <a name="fabsf"></a><a name="fabsf"></a> fabsf

傳回引數的絕對值。

```cpp
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的絕對值。

## <a name="floor"></a><a name="floor"></a> 地板

計算引數的樓層

```cpp
inline float floor(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的基底

## <a name="floorf"></a><a name="floorf"></a> floorf

計算引數的樓層

```cpp
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的基底

## <a name="fmax"></a><a name="fmax"></a> fmax

判斷引數的最大數值

```cpp
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

傳回引數的最大數值

## <a name="fmaxf"></a><a name="fmaxf"></a> fmaxf

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

## <a name="fmin"></a><a name="fmin"></a> fmin

判斷引數的最小數值

```cpp
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

## <a name="fminf"></a><a name="fminf"></a> fminf

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

## <a name="fmod"></a><a name="fmod"></a> fmod

計算 _X/_Y 的浮點餘數

```cpp
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

傳回 _X/_Y 的浮點餘數

## <a name="fmodf"></a><a name="fmodf"></a> fmodf

計算 _X/_Y 的浮點餘數。

```cpp
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

傳回 _X/_Y 的浮點餘數

## <a name="frexp"></a><a name="frexp"></a> frexp

取得 _X 的尾數和指數

```cpp
inline float frexp(
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

## <a name="frexpf"></a><a name="frexpf"></a> frexpf

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

## <a name="isfinite"></a><a name="isfinite"></a> isfinite

判斷引數是否具有有限值

```cpp
inline int isfinite(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

只有在引數具有有限值時，才會傳回非零值

## <a name="isinf"></a><a name="isinf"></a> isinf

判斷引數是否為無限大

```cpp
inline int isinf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

只有在引數有無限值時，才會傳回非零值

## <a name="isnan"></a><a name="isnan"></a> isnan

判斷引數是否為 NaN

```cpp
inline int isnan(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

只有在引數具有 NaN 值時，才會傳回非零值

## <a name="ldexp"></a><a name="ldexp"></a> ldexp

從尾數和指數計算實數

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值，mentissa

*_Exp*<br/>
整數指數

### <a name="return-value"></a>傳回值

傳回 _X \* 2 ^ _Exp

## <a name="ldexpf"></a><a name="ldexpf"></a> ldexpf

從尾數和指數計算實數

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值，mentissa

*_Exp*<br/>
整數指數

### <a name="return-value"></a>傳回值

傳回 _X \* 2 ^ _Exp

## <a name="log"></a><a name="log"></a> 日誌

計算引數以 e 為底數的對數

```cpp
inline float log(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數以 e 為底數的對數

## <a name="log10"></a><a name="log10"></a> log10

計算引數以10為底數的對數

```cpp
inline float log10(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數以10為底數的對數

## <a name="log10f"></a><a name="log10f"></a> log10f

計算引數以10為底數的對數

```cpp
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數以10為底數的對數

## <a name="log2"></a><a name="log2"></a> log2

計算引數的以2為底數的對數

```cpp
inline float log2(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數以2為底數的對數

## <a name="log2f"></a><a name="log2f"></a> log2f

計算引數的以2為底數的對數

```cpp
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數以10為底數的對數

## <a name="logf"></a><a name="logf"></a> logf

計算引數以 e 為底數的對數

```cpp
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數以 e 為底數的對數

## <a name="modf"></a><a name="modf"></a> modf

將 _X 分割成小數和整數部分。

```cpp
inline float modf(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Ip*<br/>
接收值的整數部分

### <a name="return-value"></a>傳回值

傳回 _X 的帶正負號小數部分

## <a name="modff"></a><a name="modff"></a> modff

將 _X 分割成小數和整數部分。

```cpp
inline float modff(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Ip*<br/>
接收值的整數部分

### <a name="return-value"></a>傳回值

傳回 _X 的帶正負號小數部分

## <a name="pow"></a><a name="pow"></a> 戰俘

計算 _Y 的乘冪 _X

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值，基底

*_Y*<br/>
浮點值、指數

### <a name="return-value"></a>傳回值

傳回 _Y 乘冪的 _X 值

## <a name="powf"></a><a name="powf"></a> powf

計算 _Y 的乘冪 _X

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

## <a name="round"></a><a name="round"></a> 輪

將 _X 四捨五入至最接近的整數

```cpp
inline float round(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回最接近的整數 _X

## <a name="roundf"></a><a name="roundf"></a> roundf

將 _X 四捨五入至最接近的整數

```cpp
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回最接近的整數 _X

## <a name="rsqrt"></a><a name="rsqrt"></a> rsqrt

傳回引數平方根的倒數

```cpp
inline float rsqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數平方根的倒數

## <a name="rsqrtf"></a><a name="rsqrtf"></a> rsqrtf

傳回引數平方根的倒數

```cpp
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數平方根的倒數

## <a name="signbit"></a><a name="signbit"></a> signbit

判斷 _X 的正負號是否為負數

```cpp
inline int signbit(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

只有在 _X 的正負號為負數時，才會傳回非零值

## <a name="signbitf"></a><a name="signbitf"></a> signbitf

判斷 _X 的正負號是否為負數

```cpp
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

只有在 _X 的正負號為負數時，才會傳回非零值

## <a name="sin"></a><a name="sin"></a> 罪

計算引數的正弦值

```cpp
inline float sin(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的正弦值

## <a name="sinf"></a><a name="sinf"></a> sinf

計算引數的正弦值

```cpp
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的正弦值

## <a name="sincos"></a><a name="sincos"></a> sincos

計算 _X 的正弦和余弦值

```cpp
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
傳回 _X 的余弦值

## <a name="sincosf"></a><a name="sincosf"></a> sincosf

計算 _X 的正弦和余弦值

```cpp
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
傳回 _X 的余弦值

## <a name="sinh"></a><a name="sinh"></a> sinh

計算引數的雙曲正弦值

```cpp
inline float sinh(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的雙曲正弦值

## <a name="sinhf"></a><a name="sinhf"></a> sinhf

計算引數的雙曲正弦值

```cpp
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的雙曲正弦值

## <a name="sqrt"></a><a name="sqrt"></a> sqrt

計算引數的 squre 根目錄

```cpp
inline float sqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的 squre 根目錄

## <a name="sqrtf"></a><a name="sqrtf"></a> sqrtf

計算引數的 squre 根目錄

```cpp
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的 squre 根目錄

## <a name="tan"></a><a name="tan"></a> 潭

計算引數的正切值

```cpp
inline float tan(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的正切值

## <a name="tanf"></a><a name="tanf"></a> tanf

計算引數的正切值

```cpp
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的正切值

## <a name="tanh"></a><a name="tanh"></a> tanh

計算引數的雙曲正切值

```cpp
inline float tanh(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的雙曲正切值。

## <a name="tanhf"></a><a name="tanhf"></a> tanhf

計算引數的雙曲正切值

```cpp
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的雙曲正切值。

## <a name="trunc"></a><a name="trunc"></a> trunc

截斷整陣列件的引數

```cpp
inline float trunc(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的整陣列件

## <a name="truncf"></a><a name="truncf"></a> truncf

截斷整陣列件的引數

```cpp
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回引數的整陣列件

## <a name="requirements"></a>規格需求

**Header：** Amp_math .H **命名空間：** Concurrency：： fast_math

## <a name="see-also"></a>另請參閱

[Concurrency::fast_math 命名空間](concurrency-fast-math-namespace.md)
