---
title: "Concurrency:: precise_math 命名空間函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
ms.assetid: fae53ab4-d1c5-45bb-a6a0-a74258e9aea3
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2f11d008afed6743594043ee2dd95d98c09f5505
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="concurrencyprecisemath-namespace-functions"></a>Concurrency:: precise_math 命名空間函式
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
  
##  <a name="acos"></a> acos  
 計算引數的反餘弦  
  
```  
inline float acos(float _X) restrict(amp);

 
inline double acos(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的反餘弦值  
  
##  <a name="acosf"></a>acosf  
 計算引數的反餘弦  
  
```  
inline float acosf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的反餘弦值  
  
##  <a name="acosh"></a>acosh  
 計算引數的反雙曲餘弦  
  
```  
inline float acosh(float _X) restrict(amp);

 
inline double acosh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的反雙曲餘弦值  
  
##  <a name="acoshf"></a>acoshf  
 計算引數的反雙曲餘弦  
  
```  
inline float acoshf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的反雙曲餘弦值  
  
##  <a name="asin"></a>  asin  
 計算引數的反正弦  
  
```  
inline float asin(float _X) restrict(amp);

 
inline double asin(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的反正弦值  
  
##  <a name="asinf"></a>asinf  
 計算引數的反正弦  
  
```  
inline float asinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的反正弦值  
  
##  <a name="asinh"></a>asinh  
 計算引數的反雙曲正弦  
  
```  
inline float asinh(float _X) restrict(amp);

 
inline double asinh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的反雙曲正弦值  
  
##  <a name="asinhf"></a>asinhf  
 計算引數的反雙曲正弦  
  
```  
inline float asinhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的反雙曲正弦值  
  
##  <a name="atan"></a>  atan  
 計算引數的反正切  
  
```  
inline float atan(float _X) restrict(amp);

 
inline double atan(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的反正切值  
  
##  <a name="atan2"></a>  atan2  
 計算反正切平均數/_X  
  
```  
inline float atan2(
    float _Y,  
    float _X) restrict(amp);

 
inline double atan2(
    double _Y,  
    double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Y`  
 浮點值。  
  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回平均數/_X 的反正切值  
  
##  <a name="atan2f"></a>atan2f  
 計算反正切平均數/_X  
  
```  
inline float atan2f(
    float _Y,  
    float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Y`  
 浮點值。  
  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回平均數/_X 的反正切值  
  
##  <a name="atanf"></a>atanf  
 計算引數的反正切  
  
```  
inline float atanf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的反正切值  
  
##  <a name="atanh"></a>atanh  
 計算引數的反雙曲正切  
  
```  
inline float atanh(float _X) restrict(amp);

 
inline double atanh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的反雙曲正切值  
  
##  <a name="atanhf"></a>atanhf  
 計算引數的反雙曲正切  
  
```  
inline float atanhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的反雙曲正切值  
  
##  <a name="cbrt"></a>cbrt  
 計算引數的實際的立方根  
  
```  
inline float cbrt(float _X) restrict(amp);

 
inline double cbrt(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的實際的立方根  
  
##  <a name="cbrtf"></a>cbrtf  
 計算引數的實際的立方根  
  
```  
inline float cbrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的實際的立方根  
  
##  <a name="ceil"></a>ceil  
 計算引數的上限  
  
```  
inline float ceil(float _X) restrict(amp);

 
inline double ceil(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的上限  
  
##  <a name="ceilf"></a>ceilf  
 計算引數的上限  
  
```  
inline float ceilf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的上限  
  
##  <a name="copysign"></a>copysign  
 會產生具有 _X 且平均數的正負號的值  
  
```  
inline float copysign(
    float _X,  
    float _Y) restrict(amp);

 
inline double copysign(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Y`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回具有 _X 且平均數的正負號的值  
  
##  <a name="copysignf"></a>copysignf  
 會產生具有 _X 且平均數的正負號的值  
  
```  
inline float copysignf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Y`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回具有 _X 且平均數的正負號的值  
  
##  <a name="cos"></a>  cos  
 計算引數的餘弦  
  
```  
inline float cos(float _X) restrict(amp);

 
inline double cos(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的餘弦值  
  
##  <a name="cosf"></a>cosf  
 計算引數的餘弦  
  
```  
inline float cosf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的餘弦值  
  
##  <a name="cosh"></a>  cosh  
 計算引數的雙曲餘弦值  
  
```  
inline float cosh(float _X) restrict(amp);

 
inline double cosh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的雙曲餘弦值  
  
##  <a name="coshf"></a>coshf  
 計算引數的雙曲餘弦值  
  
```  
inline float coshf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的雙曲餘弦值  
  
##  <a name="cospi"></a>cospi  
 會計算 pi 的餘弦值 * _X  
  
```  
inline float cospi(float _X) restrict(amp);

 
inline double cospi(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 pi 的餘弦值 * _X  
  
##  <a name="cospif"></a>cospif  
 會計算 pi 的餘弦值 * _X  
  
```  
inline float cospif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 pi 的餘弦值 * _X  
  
##  <a name="erf"></a>erf  
 計算 _X 錯誤函式  
  
```  
inline float erf(float _X) restrict(amp);

 
inline double erf(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 _X 錯誤函式  
  
##  <a name="erfc"></a>erfc  
 計算 _X 補充錯誤函式  
  
```  
inline float erfc(float _X) restrict(amp);

 
inline double erfc(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回互補誤差函數的 _X  
  
##  <a name="erfcf"></a>erfcf  
 計算 _X 補充錯誤函式  
  
```  
inline float erfcf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回互補誤差函數的 _X  
  
##  <a name="erfcinv"></a>erfcinv  
 計算 _X 反向的補充錯誤函式  
  
```  
inline float erfcinv(float _X) restrict(amp);

 
inline double erfcinv(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 _X 反向的補充錯誤函式  
  
##  <a name="erfcinvf"></a>erfcinvf  
 計算 _X 反向的補充錯誤函式  
  
```  
inline float erfcinvf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 _X 反向的補充錯誤函式  
  
##  <a name="erff"></a>erff  
 計算 _X 錯誤函式  
  
```  
inline float erff(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 _X 錯誤函式  
  
##  <a name="erfinv"></a>erfinv  
 計算 _X 反向錯誤函式  
  
```  
inline float erfinv(float _X) restrict(amp);

 
inline double erfinv(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 _X 反向錯誤函式  
  
##  <a name="erfinvf"></a>erfinvf  
 計算 _X 反向錯誤函式  
  
```  
inline float erfinvf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 _X 反向錯誤函式  
  
##  <a name="exp10"></a>exp10  
 計算指數引數的基底為 10  
  
```  
inline float exp10(float _X) restrict(amp);

 
inline double exp10(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回基底 10 引數的指數  
  
##  <a name="exp10f"></a>exp10f  
 計算指數引數的基底為 10  
  
```  
inline float exp10f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回基底 10 引數的指數  
  
##  <a name="expm1"></a>expm1  
 計算引數以 e 為底數的指數，減 1。  
  
```  
inline float expm1(float exponent) restrict(amp);

 
inline double expm1(double exponent) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `exponent`  
 指數詞彙 *n* 的數學運算式`e` <sup> n </sup>，其中`e`是自然對數的基底。  
  
### <a name="return-value"></a>傳回值  
 傳回引數以 e 為底數的指數，減 1。  
  
##  <a name="expm1f"></a>expm1f  
 計算引數以 e 為底數的指數，減 1。  
  
```  
inline float expm1f(float exponent) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `exponent`  
 指數詞彙 *n* 的數學運算式`e` <sup> n </sup>，其中`e`是自然對數的基底。  
  
### <a name="return-value"></a>傳回值  
 傳回引數以 e 為底數的指數，減 1。  
  
##  <a name="exp"></a>  exp  
 計算以 e 為底數的引數的指數  
  
```  
inline float exp(float _X) restrict(amp);

 
inline double exp(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回以 e 為底數的指數的引數  
  
##  <a name="expf"></a>expf  
 計算以 e 為底數的引數的指數  
  
```  
inline float expf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回以 e 為底數的指數的引數  
  
##  <a name="exp2"></a>exp2  
 計算基底 2 指數的引數  
  
```  
inline float exp2(float _X) restrict(amp);

 
inline double exp2(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回基底 2 指數的引數  
  
##  <a name="exp2f"></a>exp2f  
 計算基底 2 指數的引數  
  
```  
inline float exp2f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回基底 2 指數的引數  
  
##  <a name="fabs"></a>fabs  
 傳回引數的絕對值  
  
```  
inline float fabs(float _X) restrict(amp);

 
inline double fabs(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的絕對值  
  
##  <a name="fabsf"></a>fabsf  
 傳回引數的絕對值  
  
```  
inline float fabsf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的絕對值  

## <a name="fdim"></a>fdim  
計算引數之間的正差異。
```  
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
`_X`浮點值`_Y`浮點值。


### <a name="return-value"></a>傳回值
_X 和平均數 _X 是否大於平均數; 之間的差異否則，+ 0。
 
## <a name="fdimf"></a>fdimf  
計算引數之間的正差異。
```
inline float fdimf(
   float _X,
   float _Y
) restrict(amp);
```
### <a name="parameters"></a>參數
`_X`浮點值`_Y`浮點值。

### <a name="return-value"></a>傳回值
_X 和平均數 _X 是否大於平均數; 之間的差異否則，+ 0。 
  
##  <a name="floor"></a>floor  
 計算引數的最低限度值  
  
```  
inline float floor(float _X) restrict(amp);

 
inline double floor(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的最低限度值  
  
##  <a name="floorf"></a>floorf  
 計算引數的最低限度值  
  
```  
inline float floorf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的最低限度值  

## <a name="a-namefma-fma"></a><a name="fma">fma  
會計算產品的第一個和第二個指定的引數，然後將第三個指定的引數加入至結果。整個計算都會當做單一作業執行。
```
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
`_X`第一個浮點引數。
`_Y`第二個浮點引數。
`_Z`第三個浮點引數。

### <a name="return-value"></a>傳回值
運算式的結果 (_X * 平均數) + _Z。 整個計算會執行成單一作業。也就是說，子運算式會計算，以無限的精確度，而且最終的結果會捨入。 

## <a name="fmaf"></a>fmaf  
會計算產品的第一個和第二個指定的引數，然後將第三個指定的引數加入至結果。整個計算都會當做單一作業執行。
```
inline float fmaf(
   float _X,
   float _Y,
   float _Z
) restrict(amp);
```  
### <a name="parameters"></a>參數
`_X`第一個浮點引數。
`_Y`第二個浮點引數。
`_Z`第三個浮點引數。

### <a name="return-value"></a>傳回值
運算式的結果 (_X * 平均數) + _Z。 整個計算會執行成單一作業。也就是說，子運算式會計算，以無限的精確度，而且最終的結果會捨入。
  
##  <a name="fmax"></a>fmax  
 判斷的最大的數值引數  
  
```  
inline float fmax(
    float _X,  
    float _Y) restrict(amp);

 
inline double fmax(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Y`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回的最大的數值引數  
  
##  <a name="fmaxf"></a>fmaxf  
 判斷的最大的數值引數  
  
```  
inline float fmaxf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Y`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回的最大的數值引數  
  
##  <a name="fmin"></a>fmin  
 判斷引數的最小數值  
  
```  
inline float fmin(
    float _X,  
    float _Y) restrict(amp);

 
inline double fmin(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Y`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的最小數值  
  
##  <a name="fminf"></a>fminf  
 判斷引數的最小數值  
  
```  
inline float fminf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Y`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的最小數值  
  
##  <a name="fmod"></a>fmod 函式 (c + + AMP)  
 計算第一個指定的引數除以第二個指定的引數的其餘部分。  
  
```  
inline float fmod(
    float _X,  
    float _Y) restrict(amp);

 
inline double fmod(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 第一個浮點引數。  
  
 `_Y`  
 第二個浮點引數。  
  
### <a name="return-value"></a>傳回值  
 其餘部分`_X`除以`_Y`; 也就是值`_X`  -  `_Y`  *n* ，其中 *n* 是整數，範圍`_X`  -  `_Y`  *n* 小於幅度`_Y`。  
  
##  <a name="fmodf"></a>fmodf  
 計算第一個指定的引數除以第二個指定的引數的其餘部分。  
  
```  
inline float fmodf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 第一個浮點引數。  
  
 `_Y`  
 第二個浮點引數。  
  
### <a name="return-value"></a>傳回值  
 其餘部分`_X`除以`_Y`; 也就是值`_X`  -  `_Y`  *n* ，其中 *n* 是整數，範圍`_X`  -  `_Y`  *n* 小於幅度`_Y`。  
  
##  <a name="fpclassify"></a>fpclassify  
 將分類的引數值，為 NaN、 無限，normal subnormal，零  
  
```  
inline int fpclassify(float _X) restrict(amp);

 
inline int fpclassify(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回數字分類巨集的值適用於引數的值。  
  
##  <a name="frexp"></a>frexp  
 取得的尾數和指數的 _X  
  
```  
inline float frexp(
    float _X,  
    _Out_ int* _Exp) restrict(amp);

 
inline double frexp(
    double _X,  
    _Out_ int* _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Exp`  
 傳回的整數指數的 _X 在浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回尾數 _X  
  
##  <a name="frexpf"></a>frexpf  
 取得的尾數和指數的 _X  
  
```  
inline float frexpf(
    float _X,  
    _Out_ int* _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Exp`  
 傳回的整數指數的 _X 在浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回尾數 _X  
  
##  <a name="hypot"></a>hypot  
 計算平方的 _X 和平均數的平方根  
  
```  
inline float hypot(
    float _X,  
    float _Y) restrict(amp);

 
inline double hypot(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Y`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 _X 和平均數的平方總和的平方根  
  
##  <a name="hypotf"></a>hypotf  
 計算平方的 _X 和平均數的平方根  
  
```  
inline float hypotf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Y`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 _X 和平均數的平方總和的平方根  
  
##  <a name="ilogb"></a>ilogb  
 擷取 _X 指數做為帶正負號的 int 值  
  
```  
inline int ilogb(float _X) restrict(amp);

 
inline int ilogb(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回做為帶正負號的 int 值 _X 指數  
  
##  <a name="ilogbf"></a>ilogbf  
 擷取 _X 指數做為帶正負號的 int 值  
  
```  
inline int ilogbf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回做為帶正負號的 int 值 _X 指數  
  
##  <a name="isfinite"></a>isfinite  
 決定是否引數的有限值  
  
```  
inline int isfinite(float _X) restrict(amp);

 
inline int isfinite(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回非零值，並僅有的引數具有有限的值  
  
##  <a name="isinf"></a>isinf  
 判斷是否引數為無限  
  
```  
inline int isinf(float _X) restrict(amp);

 
inline int isinf(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回非零值，並僅有引數的無限值  
  
##  <a name="isnan"></a>isnan  
 判斷引數是否為 NaN  
  
```  
inline int isnan(float _X) restrict(amp);

 
inline int isnan(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回非零值，並僅有的引數具有 NaN 值  
  
##  <a name="isnormal"></a>isnormal  
 判斷引數是否為一般  
  
```  
inline int isnormal(float _X) restrict(amp);

 
inline int isnormal(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回非零值，並僅有的引數具有一般的值  
  
##  <a name="ldexp"></a>ldexp  
 計算實數從指定的尾數和指數。  
  
```  
inline float ldexp(
    float _X,  
    int _Exp) restrict(amp);

 
inline double ldexp(
    double _X,  
    double _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值尾數  
  
 `_Exp`  
 整數值、 指數  
  
### <a name="return-value"></a>傳回值  
 傳回 _X * 2 ^ _Exp  
  
##  <a name="ldexpf"></a>ldexpf  
 計算實數從指定的尾數和指數。  
  
```  
inline float ldexpf(
    float _X,  
    int _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值尾數  
  
 `_Exp`  
 整數值、 指數  
  
### <a name="return-value"></a>傳回值  
 傳回 _X * 2 ^ _Exp  
  
##  <a name="lgamma"></a>lgamma  
 計算絕對值的 gamma 引數的自然對數  
  
```  
inline float lgamma(
    float _X,  
    _Out_ int* _Sign) restrict(amp);

 
inline double lgamma(
    double _X,  
    _Out_ int* _Sign) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Sign`  
 傳回正負號  
  
### <a name="return-value"></a>傳回值  
 傳回 gamma 引數的絕對值的自然對數  
  
##  <a name="lgammaf"></a>lgammaf  
 計算絕對值的 gamma 引數的自然對數  
  
```  
inline float lgammaf(
    float _X,  
    _Out_ int* _Sign) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Sign`  
 傳回正負號  
  
### <a name="return-value"></a>傳回值  
 傳回 gamma 引數的絕對值的自然對數  
  
##  <a name="log"></a>  log  
 計算引數的基底 e 對數  
  
```  
inline float log(float _X) restrict(amp);

 
inline double log(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的基底 e 對數  
  
##  <a name="log10"></a>  log10  
 計算引數的基底 10 對數  
  
```  
inline float log10(float _X) restrict(amp);

 
inline double log10(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的基底 10 對數  
  
##  <a name="log10f"></a>log10f  
 計算引數的基底 10 對數  
  
```  
inline float log10f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的基底 10 對數  
  
##  <a name="log1p"></a>log1p  
 計算 1 加上引數的基底 e 對數  
  
```  
inline float log1p(float _X) restrict(amp);

 
inline double log1p(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回以 e 為底數的對數 1 加上引數  
  
##  <a name="log1pf"></a>log1pf  
 計算 1 加上引數的基底 e 對數  
  
```  
inline float log1pf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回以 e 為底數的對數 1 加上引數  
  
##  <a name="log2"></a>log2  
 計算引數的底數-2 對數  
  
```  
inline float log2(float _X) restrict(amp);

 
inline double log2(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的基底 10 對數  
  
##  <a name="log2f"></a>log2f  
 計算引數的底數-2 對數  
  
```  
inline float log2f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的基底 10 對數  
  
##  <a name="logb"></a>logb  
 擷取成浮點數格式的帶正負號的整數值 _X 指數  
  
```  
inline float logb(float _X) restrict(amp);

 
inline double logb(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回的 _X 帶正負號的指數  
  
##  <a name="logbf"></a>logbf  
 擷取成浮點數格式的帶正負號的整數值 _X 指數  
  
```  
inline float logbf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回的 _X 帶正負號的指數  
  
##  <a name="logf"></a>logf  
 計算引數的基底 e 對數  
  
```  
inline float logf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的基底 e 對數  
  
##  <a name="modf"></a>modf  
 分割分數到指定的引數和整數部分。  
  
```  
inline float modf(
    float _X,  
    _Out_ float* _Iptr) restrict(amp);

 
inline double modf(
    double _X,  
    _Out_ double* _Iptr) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Iptr`(out 參數）  
 整數部分`_X`，為浮點值。  
  
### <a name="return-value"></a>傳回值  
 帶正負號的小數部分的`_X`。  
  
##  <a name="modff"></a>modff  
 分割分數到指定的引數和整數部分。  
  
```  
inline float modff(
    float _X,  
    _Out_ float* _Iptr) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Iptr`  
 整數部分`_X`，為浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回的帶正負號的小數部分`_X`。  
  
##  <a name="nan"></a>nan  
 傳回無訊息 NaN  
  
```  
inline double nan(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 整數值  
  
### <a name="return-value"></a>傳回值  
 如果可用內容所示 _X，傳回無訊息 NaN、  
  
##  <a name="nanf"></a>nanf  
 傳回無訊息 NaN  
  
```  
inline float nanf(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 整數值  
  
### <a name="return-value"></a>傳回值  
 如果可用內容所示 _X，傳回無訊息 NaN、  
  
##  <a name="nearbyint"></a>nearbyint  
 捨入浮點格式，使用目前的捨入方向的整數值的引數。  
  
```  
inline float nearbyint(float _X) restrict(amp);

 
inline double nearbyint(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回捨入的整數值。  
  
##  <a name="nearbyintf"></a>nearbyintf  
 捨入浮點格式，使用目前的捨入方向的整數值的引數。  
  
```  
inline float nearbyintf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回捨入的整數值。  
  
##  <a name="nextafter"></a>nextafter  
 之後的平均數方向 _X 判斷下一步 表示值，函式的類型  
  
```  
inline float nextafter(
    float _X,  
    float _Y) restrict(amp);

 
inline double nextafter(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Y`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 下一步 表示值，函式的類型會在之後傳回 _X 平均數的方向  
  
##  <a name="nextafterf"></a>nextafterf  
 之後的平均數方向 _X 判斷下一步 表示值，函式的類型  
  
```  
inline float nextafterf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Y`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 下一步 表示值，函式的類型會在之後傳回 _X 平均數的方向  
  
##  <a name="phi"></a>phi  
 會傳回累計分佈函數的引數  
  
```  
inline float phi(float _X) restrict(amp);

 
inline double phi(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 會傳回累計分佈函數的引數  
  
##  <a name="phif"></a>phif  
 會傳回累計分佈函數的引數  
  
```  
inline float phif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 會傳回累計分佈函數的引數  
  
##  <a name="pow"></a>  pow  
 計算 _X 的乘冪的平均數  
  
```  
inline float pow(
    float _X,  
    float _Y) restrict(amp);

 
inline double pow(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值，基底  
  
 `_Y`  
 浮點值、 指數  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="powf"></a>powf  
 計算 _X 的乘冪的平均數  
  
```  
inline float powf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值，基底  
  
 `_Y`  
 浮點值、 指數  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="probit"></a>probit  
 傳回反向累積分佈函數的引數  
  
```  
inline float probit(float _X) restrict(amp);

 
inline double probit(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回反向累積分佈函數的引數  
  
##  <a name="probitf"></a>probitf  
 傳回反向累積分佈函數的引數  
  
```  
inline float probitf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回反向累積分佈函數的引數  
  
##  <a name="rcbrt"></a>rcbrt  
 傳回對等的引數的立方根  
  
```  
inline float rcbrt(float _X) restrict(amp);

 
inline double rcbrt(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回對等的引數的立方根  
  
##  <a name="rcbrtf"></a>rcbrtf  
 傳回對等的引數的立方根  
  
```  
inline float rcbrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回對等的引數的立方根  
  
##  <a name="remainder"></a>餘數  
 計算餘數： _X REM 平均數  
  
```  
inline float remainder(
    float _X,  
    float _Y) restrict(amp);

 
inline double remainder(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Y`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 _X REM 平均數  
  
##  <a name="remainderf"></a>remainderf  
 計算餘數： _X REM 平均數  
  
```  
inline float remainderf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Y`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 _X REM 平均數  
  
##  <a name="remquo"></a>remquo  
 計算第一個指定的引數除以第二個指定的引數的其餘部分。 也會計算第一個指定的引數除以第二個指定的引數的有效數字的有效數字的商數，並傳回商數使用第三個引數中指定的位置。  
  
```  
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
 `_X`  
 第一個浮點引數。  
  
 `_Y`  
 第二個浮點引數。  
  
 `_Quo`(out 參數）  
 用來傳回商數的分數的位元的整數的位址`_X`除以小數的位元的`_Y`。  
  
### <a name="return-value"></a>傳回值  
 傳回的其餘部分`_X`除以`_Y`。  
  
##  <a name="remquof"></a>remquof  
 計算第一個指定的引數除以第二個指定的引數的其餘部分。 也會計算第一個指定的引數除以第二個指定的引數的有效數字的有效數字的商數，並傳回商數使用第三個引數中指定的位置。  
  
```  
inline float remquof(
    float _X,  
    float _Y,  
    _Out_ int* _Quo) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 第一個浮點引數。  
  
 `_Y`  
 第二個浮點引數。  
  
 `_Quo`(out 參數）  
 用來傳回商數的分數的位元的整數的位址`_X`除以小數的位元的`_Y`。  
  
### <a name="return-value"></a>傳回值  
 傳回的其餘部分`_X`除以`_Y`。  
  
##  <a name="round"></a>捨入  
 四捨五入為最接近整數 _X  
  
```  
inline float round(float _X) restrict(amp);

 
inline double round(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回最接近的整數的 _X  
  
##  <a name="roundf"></a>roundf  
 四捨五入為最接近整數 _X  
  
```  
inline float roundf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回最接近的整數的 _X  
  
##  <a name="rsqrt"></a>rsqrt  
 傳回對等的引數的平方根  
  
```  
inline float rsqrt(float _X) restrict(amp);

 
inline double rsqrt(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回對等的引數的平方根  
  
##  <a name="rsqrtf"></a>rsqrtf  
 傳回對等的引數的平方根  
  
```  
inline float rsqrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回對等的引數的平方根  
  
##  <a name="scalb"></a>scalb  
 乘以 _X FLT_RADIX 所要電源平均數  
  
```  
inline float scalb(
    float _X,  
    float _Y) restrict(amp);

 
inline double scalb(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Y`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 _X * (FLT_RADIX ^ 平均數)  
  
##  <a name="scalbf"></a>scalbf  
 乘以 _X FLT_RADIX 所要電源平均數  
  
```  
inline float scalbf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Y`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 _X * (FLT_RADIX ^ 平均數)  
  
##  <a name="scalbn"></a>scalbn  
 乘以 _X FLT_RADIX 所要電源平均數  
  
```  
inline float scalbn(
    float _X,  
    int _Y) restrict(amp);

 
inline double scalbn(
    double _X,  
    int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Y`  
 整數值  
  
### <a name="return-value"></a>傳回值  
 傳回 _X * (FLT_RADIX ^ 平均數)  
  
##  <a name="scalbnf"></a>scalbnf  
 乘以 _X FLT_RADIX 所要電源平均數  
  
```  
inline float scalbnf(
    float _X,  
    int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Y`  
 整數值  
  
### <a name="return-value"></a>傳回值  
 傳回 _X * (FLT_RADIX ^ 平均數)  
  
##  <a name="signbit"></a>signbit  
 判斷是否 _X 的正負號為負數  
  
```  
inline int signbit(float _X) restrict(amp);

 
inline int signbit(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回非零值，如果且只有 _X 的正負號為負數  
  
##  <a name="signbitf"></a>signbitf  
 判斷是否 _X 的正負號為負數  
  
```  
inline int signbitf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回非零值，如果且只有 _X 的正負號為負數  
  
##  <a name="sin"></a>  sin  
 計算引數的正弦值  
  
```  
inline float sin(float _X) restrict(amp);

 
inline double sin(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的正弦值  
  
##  <a name="sinf"></a>sinf  
 計算引數的正弦值  
  
```  
inline float sinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的正弦值  
  
##  <a name="sincos"></a>sincos  
 計算正弦函數 」 與 「 餘弦值 _X  
  
```  
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
 `_X`  
 浮點值。  
  
 `_S`  
 傳回正弦函數值 _X  
  
 `_C`  
 傳回 _X 的餘弦值  
  
##  <a name="sincosf"></a>sincosf  
 計算正弦函數 」 與 「 餘弦值 _X  
  
```  
inline void sincosf(
    float _X,  
    _Out_ float* _S,  
    _Out_ float* _C) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_S`  
 傳回正弦函數值 _X  
  
 `_C`  
 傳回 _X 的餘弦值  
  
##  <a name="sinh"></a>  sinh  
 計算引數的雙曲正弦值  
  
```  
inline float sinh(float _X) restrict(amp);

 
inline double sinh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的雙曲正弦值  
  
##  <a name="sinhf"></a>sinhf  
 計算引數的雙曲正弦值  
  
```  
inline float sinhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的雙曲正弦值  
  
##  <a name="sinpi"></a>sinpi  
 會計算 pi 的正弦值 * _X  
  
```  
inline float sinpi(float _X) restrict(amp);

 
inline double sinpi(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 pi 的正弦值 * _X  
  
##  <a name="sinpif"></a>sinpif  
 會計算 pi 的正弦值 * _X  
  
```  
inline float sinpif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 pi 的正弦值 * _X  
  
##  <a name="sqrt"></a>  sqrt  
 計算引數的 squre 根目錄  
  
```  
inline float sqrt(float _X) restrict(amp);

 
inline double sqrt(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的 squre 根目錄  
  
##  <a name="sqrtf"></a>sqrtf  
 計算引數的 squre 根目錄  
  
```  
inline float sqrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的 squre 根目錄  
  
##  <a name="tan"></a>  tan  
 計算引數的正切函數的值  
  
```  
inline float tan(float _X) restrict(amp);

 
inline double tan(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回正切函數的引數的值  
  
##  <a name="tanf"></a>tanf  
 計算引數的正切函數的值  
  
```  
inline float tanf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回正切函數的引數的值  
  
##  <a name="tanh"></a>  tanh  
 計算引數的雙曲正切值  
  
```  
inline float tanh(float _X) restrict(amp);

 
inline double tanh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的雙曲正切值  
  
##  <a name="tanhf"></a>tanhf  
 計算引數的雙曲正切值  
  
```  
inline float tanhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的雙曲正切值  
  
##  <a name="tanpi"></a>tanpi  
 計算正切函數的 pi 值 * _X  
  
```  
inline float tanpi(float _X) restrict(amp);

 
inline double tanpi(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 pi 的正切值 * _X  
  
##  <a name="tanpif"></a>tanpif  
 計算正切函數的 pi 值 * _X  
  
```  
inline float tanpif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 pi 的正切值 * _X  
  
##  <a name="tgamma"></a>tgamma  
 計算 gamma 函數的 _X  
  
```  
inline float tgamma(float _X) restrict(amp);

 
inline double tgamma(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 gamma 函數的 _X 的結果  
  
##  <a name="tgammaf"></a>tgammaf  
 計算 gamma 函數的 _X  
  
```  
inline float tgammaf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 gamma 函數的 _X 的結果  
  
##  <a name="trunc"></a>trunc  
 截斷的整數部分的引數  
  
```  
inline float trunc(float _X) restrict(amp);

 
inline double trunc(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的整數部分  
  
##  <a name="truncf"></a>truncf  
 截斷的整數部分的引數  
  
```  
inline float truncf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的整數部分  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency::precise_math 命名空間](concurrency-precise-math-namespace.md)
