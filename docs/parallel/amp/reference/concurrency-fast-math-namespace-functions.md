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
ms.openlocfilehash: cd0882b072cfe26cd83e63024ae6837dc962ebf9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376402"
---
# <a name="concurrencyfast_math-namespace-functions"></a>Concurrency::fast_math 命名空間函式

||||
|-|-|-|
|[阿科斯](#acos)|[acosf](#acosf)|[阿辛](#asin)|
|[asinf](#asinf)|[阿坦](#atan)|[阿坦2](#atan2)|
|[atan2f](#atan2f)|[atanf](#atanf)|[塞伊爾](#ceil)|
|[ceilf](#ceilf)|[因為](#cos)|[cosf](#cosf)|
|[cosh](#cosh)|[coshf](#coshf)|[exp](#exp)|
|[exp2](#exp2)|[exp2f](#exp2f)|[expf](#expf)|
|[fabs](#fabs)|[fabsf](#fabsf)|[地板](#floor)|
|[floorf](#floorf)|[fmax](#fmax)|[fmaxf](#fmaxf)|
|[fmin](#fmin)|[fminf](#fminf)|[fmod](#fmod)|
|[fmodf](#fmodf)|[frexp](#frexp)|[弗雷克斯普夫](#frexpf)|
|[是有限的](#isfinite)|[是因夫](#isinf)|[isnan](#isnan)|
|[ldexp](#ldexp)|[爾德克斯普夫](#ldexpf)|[紀錄](#log)|
|[紀錄10](#log10)|[log10f](#log10f)|[紀錄2](#log2)|
|[log2f](#log2f)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[戰俘](#pow)|[powf](#powf)|
|[輪](#round)|[roundf](#roundf)|[rsqrt](#rsqrt)|
|[rsqrtf](#rsqrtf)|[signbit](#signbit)|[符號比夫](#signbitf)|
|[罪](#sin)|[辛科斯](#sincos)|[辛科斯夫](#sincosf)|
|[sinf](#sinf)|[sinh](#sinh)|[sinhf](#sinhf)|
|[sqrt](#sqrt)|[sqrtf](#sqrtf)|[潭](#tan)|
|[tanf](#tanf)|[坦赫](#tanh)|[tanhf](#tanhf)|
|[特魯恩](#trunc)|[truncf](#truncf)|

## <a name="acos"></a><a name="acos"></a>阿科斯

計算參數的弧形

```cpp
inline float acos(float _X) restrict(amp);
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

## <a name="asin"></a><a name="asin"></a>阿辛

計算參數的弧形

```cpp
inline float asin(float _X) restrict(amp);
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

## <a name="atan"></a><a name="atan"></a>阿坦

計算引數的反正切

```cpp
inline float atan(float _X) restrict(amp);
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

## <a name="ceil"></a><a name="ceil"></a>塞伊爾

計算參數的上限

```cpp
inline float ceil(float _X) restrict(amp);
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

## <a name="cos"></a><a name="cos"></a>因為

計算引數的餘弦

```cpp
inline float cos(float _X) restrict(amp);
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
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的雙曲性拋物值

## <a name="exp"></a><a name="exp"></a>exp

計算參數的基-e 指數

```cpp
inline float exp(float _X) restrict(amp);
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

## <a name="fabs"></a><a name="fabs"></a>晶圓廠

傳回參數的絕對值

```cpp
inline float fabs(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

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

## <a name="floor"></a><a name="floor"></a>地板

計算參數的層級

```cpp
inline float floor(float _X) restrict(amp);
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

## <a name="fmax"></a><a name="fmax"></a>fmax

確定參數的最大數值

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

## <a name="fmod"></a><a name="fmod"></a>弗莫德

計算_X/_Y的浮點餘數

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

返回_X/_Y的浮點餘數

## <a name="fmodf"></a><a name="fmodf"></a>fmodf

計算_X/_Y的浮點餘數。

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

返回_X/_Y的浮點餘數

## <a name="frexp"></a><a name="frexp"></a>弗雷費浦

取得_X的曼蒂薩和指數

```cpp
inline float frexp(
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

## <a name="isfinite"></a><a name="isfinite"></a>是有限的

確定參數是否具有有限值

```cpp
inline int isfinite(float _X) restrict(amp);
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
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

僅當參數具有 NaN 值時,才傳回非零值

## <a name="ldexp"></a><a name="ldexp"></a>爾德莫

計算來自曼蒂薩和指數的實數

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值,門塔薩

*_Exp*<br/>
整數指數

### <a name="return-value"></a>傳回值

返回_X \* 2+_Exp

## <a name="ldexpf"></a><a name="ldexpf"></a>爾德克斯普夫

計算來自曼蒂薩和指數的實數

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值,門塔薩

*_Exp*<br/>
整數指數

### <a name="return-value"></a>傳回值

返回_X \* 2+_Exp

## <a name="log"></a><a name="log"></a>紀錄

計算參數的基數-e對數

```cpp
inline float log(float _X) restrict(amp);
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

## <a name="log2"></a><a name="log2"></a>紀錄2

計算參數的基 2 對數

```cpp
inline float log2(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回參數的基 2 對數

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

將_X拆分為小數和整數零件。

```cpp
inline float modf(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Ip*<br/>
接收值的整數部份

### <a name="return-value"></a>傳回值

傳回_X的簽名小數部份

## <a name="modff"></a><a name="modff"></a>莫德夫

將_X拆分為小數和整數零件。

```cpp
inline float modff(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

*_Ip*<br/>
接收值的整數部份

### <a name="return-value"></a>傳回值

傳回_X的簽名小數部份

## <a name="pow"></a><a name="pow"></a>戰俘

計算_X提升到_Y功率

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值,基

*_Y*<br/>
浮點值,指數

### <a name="return-value"></a>傳回值

返回_X的值,以_Y

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

## <a name="round"></a><a name="round"></a>輪

舍_X到最接近的整數

```cpp
inline float round(float _X) restrict(amp);
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

## <a name="signbit"></a><a name="signbit"></a>符號位

確定_X的符號是否為負

```cpp
inline int signbit(float _X) restrict(amp);
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
    float* _S,
    float* _C) restrict(amp);
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
    float* _S,
    float* _C) restrict(amp);
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

## <a name="sqrt"></a><a name="sqrt"></a>sqrt

計算參數的 squre 根

```cpp
inline float sqrt(float _X) restrict(amp);
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

## <a name="trunc"></a><a name="trunc"></a>特魯恩

將參數截斷到整陣元件

```cpp
inline float trunc(float _X) restrict(amp);
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

## <a name="requirements"></a>需求

**標題:** amp_math.h**命名空間:** 併發::fast_math

## <a name="see-also"></a>另請參閱

[Concurrency::fast_math 命名空間](concurrency-fast-math-namespace.md)
