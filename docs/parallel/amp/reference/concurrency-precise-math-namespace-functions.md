---
title: "Concurrency:: precise_math 命名空間函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fae53ab4-d1c5-45bb-a6a0-a74258e9aea3
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 73273a58f73860c77810a6ab59def560962f9539
ms.lasthandoff: 02/24/2017

---
# <a name="concurrencyprecisemath-namespace-functions"></a>Concurrency:: precise_math 命名空間函式
||||  
|-|-|-|  
|[acos 函式](#acos)|[acosf 函式](#acosf)|[acosh 函式](#acosh)|  
|[acoshf 函式](#acoshf)|[asin 函式](#asin)|[asinf 函式](#asinf)|  
|[asinh 函式](#asinh)|[asinhf 函式](#asinhf)|[atan 函式](#atan)|  
|[atan2 函式](#atan2)|[atan2f 函式](#atan2f)|[atanf 函式](#atanf)|  
|[atanh 函式](#atanh)|[atanhf 函式](#atanhf)|[cbrt 函式](#cbrt)|  
|[cbrtf 函式](#cbrtf)|[ceil 函式](#ceil)|[ceilf 函式](#ceilf)|  
|[copysign 函式](#copysign)|[copysignf 函式](#copysignf)|[cos 函式](#cos)|  
|[cosf 函式](#cosf)|[cosh 函式](#cosh)|[coshf 函式](#coshf)|  
|[cospi 函式](#cospi)|[cospif 函式](#cospif)|[erf 函式](#erf)|  
|[erfc 函式](#erfc)|[erfcf 函式](#erfcf)|[erfcinv 函式](#erfcinv)|  
|[erfcinvf 函式](#erfcinvf)|[erff 函式](#erff)|[erfinv 函式](#erfinv)|  
|[erfinvf 函式](#erfinvf)|[exp 函式](#exp)|[exp10 函式](#exp10)|  
|[exp10f 函式](#exp10f)|[exp2 函式](#exp2)|[exp2f 函式](#exp2f)|  
|[expf 函式](#expf)|[expm1 函式](#expm1)|[expm1f 函式](#expm1f)|  
|[fabs 函式](#fabs)|[fabsf 函式](#fabsf)|[floor 函式](#floor)| 
|[fdim 函式](#fdim)|[fdimf 函式](#fdimf)|| 
|[floorf 函式](#floorf)|[fma 函式](#fma)|[fmaf 函式](#fmaf)|
[fmax 函式](#fmax)|[fmaxf 函式](#fmaxf)|| 
|[fmin 函式](#fmin)|[fminf 函式](#fminf)|[fmod 函式](#fmod)|  
|[fmodf 函式](#fmodf)|[fpclassify 函式](#fpclassify)|[frexp 函式](#frexp)|  
|[frexpf 函式](#frexpf)|[hypot 函式](#hypot)|[hypotf 函式](#hypotf)|  
|[ilogb 函式](#ilogb)|[ilogbf 函式](#ilogbf)|[isfinite 函式](#isfinite)|  
|[isinf 函式](#isinf)|[isnan 函式](#isnan)|[isnormal 函式](#isnormal)|  
|[ldexp 函式](#ldexp)|[ldexpf 函式](#ldexpf)|[lgamma 函式](#lgamma)|  
|[lgammaf 函式](#lgammaf)|[log 函式](#log)|[log10 函式](#log10)|  
|[log10f 函式](#log10f)|[log1p 函式](#log1p)|[log1pf 函式](#log1pf)|  
|[log2 函式](#log2)|[log2f 函式](#log2f)|[logb 函式](#logb)|  
|[logbf 函式](#logbf)|[logf 函式](#logf)|[modf 函式](#modf)|  
|[modff 函式](#modff)|[nan 函式](#nan)|[nanf 函式](#nanf)|  
|[nearbyint 函式](#nearbyint)|[nearbyintf 函式](#nearbyintf)|[nextafter 函式](#nextafter)|  
|[nextafterf 函式](#nextafterf)|[phi 函式](#phi)|[phif 函式](#phif)|  
|[pow 函式](#pow)|[powf 函式](#powf)|[probit 函式](#probit)|  
|[probitf 函式](#probitf)|[rcbrt 函式](#rcbrt)|[rcbrtf 函式](#rcbrtf)|  
|[remainder 函式](#remainder)|[remainderf 函式](#remainderf)|[remquo 函式](#remquo)|  
|[remquof 函式](#remquof)|[round 函式](#round)|[roundf 函式](#roundf)|  
|[rsqrt 函式](#rsqrt)|[rsqrtf 函式](#rsqrtf)|[scalb 函式](#scalb)|  
|[scalbf 函式](#scalbf)|[scalbn 函式](#scalbn)|[scalbnf 函式](#scalbnf)|  
|[signbit 函式](#signbit)|[signbitf 函式](#signbitf)|[sin 函式](#sin)|  
|[sincos 函式](#sincos)|[sincosf 函式](#sincosf)|[sinf 函式](#sinf)|  
|[sinh 函式](#sinh)|[sinhf 函式](#sinhf)|[sinpi 函式](#sinpi)|  
|[sinpif 函式](#sinpif)|[sqrt 函式](#sqrt)|[sqrtf 函式](#sqrtf)|  
|[tan 函式](#tan)|[tanf 函式](#tanf)|[tanh 函式](#tanh)|  
|[tanhf 函式](#tanhf)|[tanpi 函式](#tanpi)|[tanpif 函式](#tanpif)|  
|[tgamma 函式](#tgamma)|[tgammaf 函式](#tgammaf)|[trunc 函式](#trunc)|  
|[truncf 函式](#truncf)|  
  
##  <a name="a-nameacosa--acos-function"></a><a name="acos"></a>acos 函式  
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
  
##  <a name="a-nameacosfa--acosf-function"></a><a name="acosf"></a>acosf 函式  
 計算引數的反餘弦  
  
```  
inline float acosf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的反餘弦值  
  
##  <a name="a-nameacosha--acosh-function"></a><a name="acosh"></a>acosh 函式  
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
  
##  <a name="a-nameacoshfa--acoshf-function"></a><a name="acoshf"></a>acoshf 函式  
 計算引數的反雙曲餘弦  
  
```  
inline float acoshf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的反雙曲餘弦值  
  
##  <a name="a-nameasina--asin-function"></a><a name="asin"></a>asin 函式  
 計算引數的反正弦值  
  
```  
inline float asin(float _X) restrict(amp);

 
inline double asin(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的反正弦值  
  
##  <a name="a-nameasinfa--asinf-function"></a><a name="asinf"></a>asinf 函式  
 計算引數的反正弦值  
  
```  
inline float asinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的反正弦值  
  
##  <a name="a-nameasinha--asinh-function"></a><a name="asinh"></a>asinh 函式  
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
  
##  <a name="a-nameasinhfa--asinhf-function"></a><a name="asinhf"></a>asinhf 函式  
 計算引數的反雙曲正弦  
  
```  
inline float asinhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的反雙曲正弦值  
  
##  <a name="a-nameatana--atan-function"></a><a name="atan"></a>atan 函式  
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
  
##  <a name="a-nameatan2a--atan2-function"></a><a name="atan2"></a>atan2 函式  
 計算 _Y/_X 的反正切  
  
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
 傳回 _Y/_X 的反正切值  
  
##  <a name="a-nameatan2fa--atan2f-function"></a><a name="atan2f"></a>atan2f 函式  
 計算 _Y/_X 的反正切  
  
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
 傳回 _Y/_X 的反正切值  
  
##  <a name="a-nameatanfa--atanf-function"></a><a name="atanf"></a>atanf 函式  
 計算引數的反正切  
  
```  
inline float atanf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的反正切值  
  
##  <a name="a-nameatanha--atanh-function"></a><a name="atanh"></a>atanh 函式  
 計算引數的反雙曲正切  
  
```  
inline float atanh(float _X) restrict(amp);

 
inline double atanh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的反雙曲線正切函數的值  
  
##  <a name="a-nameatanhfa--atanhf-function"></a><a name="atanhf"></a>atanhf 函式  
 計算引數的反雙曲正切  
  
```  
inline float atanhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的反雙曲線正切函數的值  
  
##  <a name="a-namecbrta--cbrt-function"></a><a name="cbrt"></a>cbrt 函式  
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
  
##  <a name="a-namecbrtfa--cbrtf-function"></a><a name="cbrtf"></a>cbrtf 函式  
 計算引數的實際的立方根  
  
```  
inline float cbrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的實際的立方根  
  
##  <a name="a-nameceila--ceil-function"></a><a name="ceil"></a>ceil 函式  
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
  
##  <a name="a-nameceilfa--ceilf-function"></a><a name="ceilf"></a>ceilf 函式  
 計算引數的上限  
  
```  
inline float ceilf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的上限  
  
##  <a name="a-namecopysigna--copysign-function"></a><a name="copysign"></a>copysign 函式  
 產生與 _X 且 _Y 的正負號的值  
  
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
 傳回具有 _X 且 _Y 的正負號的值  
  
##  <a name="a-namecopysignfa--copysignf-function"></a><a name="copysignf"></a>copysignf 函式  
 產生與 _X 且 _Y 的正負號的值  
  
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
 傳回具有 _X 且 _Y 的正負號的值  
  
##  <a name="a-namecosa--cos-function"></a><a name="cos"></a>cos 函式  
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
  
##  <a name="a-namecosfa--cosf-function"></a><a name="cosf"></a>cosf 函式  
 計算引數的餘弦  
  
```  
inline float cosf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的餘弦值  
  
##  <a name="a-namecosha--cosh-function"></a><a name="cosh"></a>cosh 函式  
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
  
##  <a name="a-namecoshfa--coshf-function"></a><a name="coshf"></a>coshf 函式  
 計算引數的雙曲餘弦值  
  
```  
inline float coshf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的雙曲餘弦值  
  
##  <a name="a-namecospia--cospi-function"></a><a name="cospi"></a>cospi 函式  
 計算 pi 的餘弦值 * _X  
  
```  
inline float cospi(float _X) restrict(amp);

 
inline double cospi(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 pi 的餘弦值 * _X  
  
##  <a name="a-namecospifa--cospif-function"></a><a name="cospif"></a>cospif 函式  
 計算 pi 的餘弦值 * _X  
  
```  
inline float cospif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 pi 的餘弦值 * _X  
  
##  <a name="a-nameerfa--erf-function"></a><a name="erf"></a>erf 函式  
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
  
##  <a name="a-nameerfca--erfc-function"></a><a name="erfc"></a>erfc 函式  
 計算 _X 補充錯誤函式  
  
```  
inline float erfc(float _X) restrict(amp);

 
inline double erfc(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 _X 補充錯誤函式  
  
##  <a name="a-nameerfcfa--erfcf-function"></a><a name="erfcf"></a>erfcf 函式  
 計算 _X 補充錯誤函式  
  
```  
inline float erfcf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 _X 補充錯誤函式  
  
##  <a name="a-nameerfcinva--erfcinv-function"></a><a name="erfcinv"></a>erfcinv 函式  
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
  
##  <a name="a-nameerfcinvfa--erfcinvf-function"></a><a name="erfcinvf"></a>erfcinvf 函式  
 計算 _X 反向的補充錯誤函式  
  
```  
inline float erfcinvf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 _X 反向的補充錯誤函式  
  
##  <a name="a-nameerffa--erff-function"></a><a name="erff"></a>erff 函式  
 計算 _X 錯誤函式  
  
```  
inline float erff(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 _X 錯誤函式  
  
##  <a name="a-nameerfinva--erfinv-function"></a><a name="erfinv"></a>erfinv 函式  
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
  
##  <a name="a-nameerfinvfa--erfinvf-function"></a><a name="erfinvf"></a>erfinvf 函式  
 計算 _X 反向錯誤函式  
  
```  
inline float erfinvf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 _X 反向錯誤函式  
  
##  <a name="a-nameexp10a--exp10-function"></a><a name="exp10"></a>exp10 函式  
 計算指數引數的基底為&10;  
  
```  
inline float exp10(float _X) restrict(amp);

 
inline double exp10(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回基底&10; 引數的指數  
  
##  <a name="a-nameexp10fa--exp10f-function"></a><a name="exp10f"></a>exp10f 函式  
 計算指數引數的基底為&10;  
  
```  
inline float exp10f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回基底&10; 引數的指數  
  
##  <a name="a-nameexpm1a--expm1-function"></a><a name="expm1"></a>expm1 函式  
 計算引數以 e 為底數的指數，減 1。  
  
```  
inline float expm1(float exponent) restrict(amp);

 
inline double expm1(double exponent) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `exponent`  
 指數詞彙*n*的數學運算式`e` <sup>n</sup>，其中`e`是自然對數的基底。  
  
### <a name="return-value"></a>傳回值  
 傳回引數以 e 為底數的指數，減 1。  
  
##  <a name="a-nameexpm1fa--expm1f-function"></a><a name="expm1f"></a>expm1f 函式  
 計算引數以 e 為底數的指數，減 1。  
  
```  
inline float expm1f(float exponent) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `exponent`  
 指數詞彙*n*的數學運算式`e` <sup>n</sup>，其中`e`是自然對數的基底。  
  
### <a name="return-value"></a>傳回值  
 傳回引數以 e 為底數的指數，減 1。  
  
##  <a name="a-nameexpa--exp-function"></a><a name="exp"></a>exp 函式  
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
  
##  <a name="a-nameexpfa--expf-function"></a><a name="expf"></a>expf 函式  
 計算以 e 為底數的引數的指數  
  
```  
inline float expf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回以 e 為底數的指數的引數  
  
##  <a name="a-nameexp2a--exp2-function"></a><a name="exp2"></a>exp2 函式  
 計算引數的指數底數-2  
  
```  
inline float exp2(float _X) restrict(amp);

 
inline double exp2(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回基底&2; 指數引數  
  
##  <a name="a-nameexp2fa--exp2f-function"></a><a name="exp2f"></a>exp2f 函式  
 計算引數的指數底數-2  
  
```  
inline float exp2f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回基底&2; 指數引數  
  
##  <a name="a-namefabsa--fabs-function"></a><a name="fabs"></a>fabs 函式  
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
  
##  <a name="a-namefabsfa--fabsf-function"></a><a name="fabsf"></a>fabsf 函式  
 傳回引數的絕對值  
  
```  
inline float fabsf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的絕對值  

## <a name="a-namefdima-fdim-function"></a><a name="fdim"></a>fdim 函式  
計算引數之間的正數的差異。
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
_X 和 _Y _X 是否大於 _Y; 之間的差異否則 +&0;。
 
## <a name="a-namefdimfa-fdimf-function"></a><a name="fdimf"></a>fdimf 函式
計算引數之間的正數的差異。
```
inline float fdimf(
   float _X,
   float _Y
) restrict(amp);
```
### <a name="parameters"></a>參數
`_X`浮點值`_Y`浮點值。

### <a name="return-value"></a>傳回值
_X 和 _Y _X 是否大於 _Y; 之間的差異否則 +&0;。 
  
##  <a name="a-namefloora--floor-function"></a><a name="floor"></a>floor 函式  
 計算引數的最低限度值  
  
```  
inline float floor(float _X) restrict(amp);

 
inline double floor(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的最低限度  
  
##  <a name="a-namefloorfa--floorf-function"></a><a name="floorf"></a>floorf 函式  
 計算引數的最低限度值  
  
```  
inline float floorf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的最低限度  

## <a name="a-namefma-fma-function"></a><a name="fma">fma 函式  
會計算產品的第一個和第二個指定的引數，然後將結果，加上第三個指定的引數整個計算是以單一作業執行。
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
`_X`第一個的浮點引數。
`_Y`第二個浮點引數。
`_Z`第三個浮點引數。

### <a name="return-value"></a>傳回值
運算式的結果 (_X * _Y) + _Z。 執行整個計算為單一作業;也就是說，子運算式會計算為無限的精確度，而且最終的結果會捨入。 

## <a name="a-namefmafa-fmaf-function"></a><a name="fmaf"></a>fmaf 函式  
會計算產品的第一個和第二個指定的引數，然後將結果，加上第三個指定的引數整個計算是以單一作業執行。
```
inline float fmaf(
   float _X,
   float _Y,
   float _Z
) restrict(amp);
```  
### <a name="parameters"></a>參數
`_X`第一個的浮點引數。
`_Y`第二個浮點引數。
`_Z`第三個浮點引數。

### <a name="return-value"></a>傳回值
運算式的結果 (_X * _Y) + _Z。 執行整個計算為單一作業;也就是說，子運算式會計算為無限的精確度，而且最終的結果會捨入。
  
##  <a name="a-namefmaxa--fmax-function"></a><a name="fmax"></a>fmax 函式  
 判斷引數的最大數值  
  
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
 傳回引數的最大的數值  
  
##  <a name="a-namefmaxfa--fmaxf-function"></a><a name="fmaxf"></a>fmaxf 函式  
 判斷引數的最大數值  
  
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
 傳回引數的最大的數值  
  
##  <a name="a-namefmina--fmin-function"></a><a name="fmin"></a>fmin 函式  
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
  
##  <a name="a-namefminfa--fminf-function"></a><a name="fminf"></a>fminf 函式  
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
  
##  <a name="a-namefmoda--fmod-function-c-amp"></a><a name="fmod"></a>fmod 函式 (c + + AMP)  
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
 第一個的浮點引數。  
  
 `_Y`  
 第二個浮點引數。  
  
### <a name="return-value"></a>傳回值  
 其餘部分`_X`除以`_Y`; 也就是值`_X`  -  `_Y` *n*，其中*n*是整數，範圍的`_X`  -  `_Y` *n*的大小小於`_Y`。  
  
##  <a name="a-namefmodfa--fmodf-function"></a><a name="fmodf"></a>fmodf 函式  
 計算第一個指定的引數除以第二個指定的引數的其餘部分。  
  
```  
inline float fmodf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 第一個的浮點引數。  
  
 `_Y`  
 第二個浮點引數。  
  
### <a name="return-value"></a>傳回值  
 其餘部分`_X`除以`_Y`; 也就是值`_X`  -  `_Y` *n*，其中*n*是整數，範圍的`_X`  -  `_Y` *n*的大小小於`_Y`。  
  
##  <a name="a-namefpclassifya--fpclassify-function"></a><a name="fpclassify"></a>fpclassify 函式  
 將引數值分類為 NaN、 無限，normal subnormal，零  
  
```  
inline int fpclassify(float _X) restrict(amp);

 
inline int fpclassify(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回數字分類巨集的值適用於引數的值。  
  
##  <a name="a-namefrexpa--frexp-function"></a><a name="frexp"></a>frexp 函式  
 取得尾數和指數 _X  
  
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
 傳回整數的指數 _X 在浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回尾數 _X  
  
##  <a name="a-namefrexpfa--frexpf-function"></a><a name="frexpf"></a>frexpf 函式  
 取得尾數和指數 _X  
  
```  
inline float frexpf(
    float _X,  
    _Out_ int* _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Exp`  
 傳回整數的指數 _X 在浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回尾數 _X  
  
##  <a name="a-namehypota--hypot-function"></a><a name="hypot"></a>hypot 函式  
 計算的 _X 和 _Y 平方總和的平方根  
  
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
 傳回的 _X 和 _Y 平方總和的平方根  
  
##  <a name="a-namehypotfa--hypotf-function"></a><a name="hypotf"></a>hypotf 函式  
 計算的 _X 和 _Y 平方總和的平方根  
  
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
 傳回的 _X 和 _Y 平方總和的平方根  
  
##  <a name="a-nameilogba--ilogb-function"></a><a name="ilogb"></a>ilogb 函式  
 擷取 _X 指數為帶正負號的 int 值  
  
```  
inline int ilogb(float _X) restrict(amp);

 
inline int ilogb(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回做為帶正負號的 int 值 _X 指數  
  
##  <a name="a-nameilogbfa--ilogbf-function"></a><a name="ilogbf"></a>ilogbf 函式  
 擷取 _X 指數為帶正負號的 int 值  
  
```  
inline int ilogbf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回做為帶正負號的 int 值 _X 指數  
  
##  <a name="a-nameisfinitea--isfinite-function"></a><a name="isfinite"></a>isfinite 函式  
 決定是否引數的有限值  
  
```  
inline int isfinite(float _X) restrict(amp);

 
inline int isfinite(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 若引數的有限值傳回非零值  
  
##  <a name="a-nameisinfa--isinf-function"></a><a name="isinf"></a>isinf 函式  
 決定是否引數是無限值  
  
```  
inline int isinf(float _X) restrict(amp);

 
inline int isinf(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 若引數的無限值，傳回非零值  
  
##  <a name="a-nameisnana--isnan-function"></a><a name="isnan"></a>isnan 函式  
 決定是否該引數是 NaN  
  
```  
inline int isnan(float _X) restrict(amp);

 
inline int isnan(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回非零值，如果且只有引數的 NaN 值  
  
##  <a name="a-nameisnormala--isnormal-function"></a><a name="isnormal"></a>isnormal 函式  
 判斷引數是否為標準模式  
  
```  
inline int isnormal(float _X) restrict(amp);

 
inline int isnormal(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回非零值，如果且只有引數的標準值  
  
##  <a name="a-nameldexpa--ldexp-function"></a><a name="ldexp"></a>ldexp 函式  
 計算從指定的尾數和指數的實際數字。  
  
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
  
##  <a name="a-nameldexpfa--ldexpf-function"></a><a name="ldexpf"></a>ldexpf 函式  
 計算從指定的尾數和指數的實際數字。  
  
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
  
##  <a name="a-namelgammaa--lgamma-function"></a><a name="lgamma"></a>lgamma 函式  
 計算自然對數的 gamma 引數的絕對值  
  
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
  
##  <a name="a-namelgammafa--lgammaf-function"></a><a name="lgammaf"></a>lgammaf 函式  
 計算自然對數的 gamma 引數的絕對值  
  
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
  
##  <a name="a-nameloga--log-function"></a><a name="log"></a>log 函式  
 計算引數以 e 為底數對數  
  
```  
inline float log(float _X) restrict(amp);

 
inline double log(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數以 e 為底數的對數  
  
##  <a name="a-namelog10a--log10-function"></a><a name="log10"></a>log10 函式  
 計算引數的基底&10; 對數  
  
```  
inline float log10(float _X) restrict(amp);

 
inline double log10(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的基底&10; 對數  
  
##  <a name="a-namelog10fa--log10f-function"></a><a name="log10f"></a>log10f 函式  
 計算引數的基底&10; 對數  
  
```  
inline float log10f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的基底&10; 對數  
  
##  <a name="a-namelog1pa--log1p-function"></a><a name="log1p"></a>log1p 函式  
 計算以 e 為底數的對數 1 再加上引數  
  
```  
inline float log1p(float _X) restrict(amp);

 
inline double log1p(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回以 e 為底數的對數 1 再加上引數  
  
##  <a name="a-namelog1pfa--log1pf-function"></a><a name="log1pf"></a>log1pf 函式  
 計算以 e 為底數的對數 1 再加上引數  
  
```  
inline float log1pf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回以 e 為底數的對數 1 再加上引數  
  
##  <a name="a-namelog2a--log2-function"></a><a name="log2"></a>log2 函式  
 計算引數的基底&2; 對數  
  
```  
inline float log2(float _X) restrict(amp);

 
inline double log2(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的基底&10; 對數  
  
##  <a name="a-namelog2fa--log2f-function"></a><a name="log2f"></a>log2f 函式  
 計算引數的基底&2; 對數  
  
```  
inline float log2f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的基底&10; 對數  
  
##  <a name="a-namelogba--logb-function"></a><a name="logb"></a>logb 函式  
 擷取 _X，指數為帶正負號的整數中的值的浮點格式  
  
```  
inline float logb(float _X) restrict(amp);

 
inline double logb(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回的 _X 帶正負號的指數  
  
##  <a name="a-namelogbfa--logbf-function"></a><a name="logbf"></a>logbf 函式  
 擷取 _X，指數為帶正負號的整數中的值的浮點格式  
  
```  
inline float logbf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回的 _X 帶正負號的指數  
  
##  <a name="a-namelogfa--logf-function"></a><a name="logf"></a>logf 函式  
 計算引數以 e 為底數對數  
  
```  
inline float logf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數以 e 為底數的對數  
  
##  <a name="a-namemodfa--modf-function"></a><a name="modf"></a>modf 函式  
 將指定的引數至小數與整數部分。  
  
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
 整數部分`_X`，做為浮點值。  
  
### <a name="return-value"></a>傳回值  
 帶正負號的小數部分的`_X`。  
  
##  <a name="a-namemodffa--modff-function"></a><a name="modff"></a>modff 函式  
 將指定的引數至小數與整數部分。  
  
```  
inline float modff(
    float _X,  
    _Out_ float* _Iptr) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Iptr`  
 整數部分`_X`，做為浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回的帶正負號的小數部分的`_X`。  
  
##  <a name="a-namenana--nan-function"></a><a name="nan"></a>nan 函式  
 傳回無訊息 NaN  
  
```  
inline double nan(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 整數值  
  
### <a name="return-value"></a>傳回值  
 如果可用內容所示 _X，傳回無訊息 NaN，  
  
##  <a name="a-namenanfa--nanf-function"></a><a name="nanf"></a>nanf 函式  
 傳回無訊息 NaN  
  
```  
inline float nanf(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 整數值  
  
### <a name="return-value"></a>傳回值  
 如果可用內容所示 _X，傳回無訊息 NaN，  
  
##  <a name="a-namenearbyinta--nearbyint-function"></a><a name="nearbyint"></a>nearbyint 函式  
 四捨五入至浮點格式，使用目前的捨入方向的整數值的引數。  
  
```  
inline float nearbyint(float _X) restrict(amp);

 
inline double nearbyint(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回捨入的整數值。  
  
##  <a name="a-namenearbyintfa--nearbyintf-function"></a><a name="nearbyintf"></a>nearbyintf 函式  
 四捨五入至浮點格式，使用目前的捨入方向的整數值的引數。  
  
```  
inline float nearbyintf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回捨入的整數值。  
  
##  <a name="a-namenextaftera--nextafter-function"></a><a name="nextafter"></a>nextafter 函式  
 判斷 _X _Y 的方向之後的下一個可顯示值，函數的類型  
  
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
 _X _Y 的方向之後，傳回的函式型別中的下一個可顯示的值，  
  
##  <a name="a-namenextafterfa--nextafterf-function"></a><a name="nextafterf"></a>nextafterf 函式  
 判斷 _X _Y 的方向之後的下一個可顯示值，函數的類型  
  
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
 _X _Y 的方向之後，傳回的函式型別中的下一個可顯示的值，  
  
##  <a name="a-namephia--phi-function"></a><a name="phi"></a>phi 函式  
 傳回累加分配函數的引數  
  
```  
inline float phi(float _X) restrict(amp);

 
inline double phi(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回累加分配函數的引數  
  
##  <a name="a-namephifa--phif-function"></a><a name="phif"></a>phif 函式  
 傳回累加分配函數的引數  
  
```  
inline float phif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回累加分配函數的引數  
  
##  <a name="a-namepowa--pow-function"></a><a name="pow"></a>pow 函式  
 計算乘冪的 _Y _X  
  
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
  
##  <a name="a-namepowfa--powf-function"></a><a name="powf"></a>powf 函式  
 計算乘冪的 _Y _X  
  
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
  
##  <a name="a-nameprobita--probit-function"></a><a name="probit"></a>probit 函式  
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
  
##  <a name="a-nameprobitfa--probitf-function"></a><a name="probitf"></a>probitf 函式  
 傳回反向累積分佈函數的引數  
  
```  
inline float probitf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回反向累積分佈函數的引數  
  
##  <a name="a-namercbrta--rcbrt-function"></a><a name="rcbrt"></a>rcbrt 函式  
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
  
##  <a name="a-namercbrtfa--rcbrtf-function"></a><a name="rcbrtf"></a>rcbrtf 函式  
 傳回對等的引數的立方根  
  
```  
inline float rcbrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回對等的引數的立方根  
  
##  <a name="a-nameremaindera--remainder-function"></a><a name="remainder"></a>remainder 函式  
 計算餘數︰ _X REM _Y  
  
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
 傳回 _X REM _Y  
  
##  <a name="a-nameremainderfa--remainderf-function"></a><a name="remainderf"></a>remainderf 函式  
 計算餘數︰ _X REM _Y  
  
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
 傳回 _X REM _Y  
  
##  <a name="a-nameremquoa--remquo-function"></a><a name="remquo"></a>remquo 函式  
 計算第一個指定的引數除以第二個指定的引數的其餘部分。 同時計算第一個指定的引數除以第二個指定之引數的有效數字的有效數字的商數，並傳回商數使用第三個引數中指定的位置。  
  
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
 第一個的浮點引數。  
  
 `_Y`  
 第二個浮點引數。  
  
 `_Quo`(out 參數）  
 用來傳回小數的位元的商數的整數的位址`_X`除以小數的位元的`_Y`。  
  
### <a name="return-value"></a>傳回值  
 傳回的其餘部分`_X`除以`_Y`。  
  
##  <a name="a-nameremquofa--remquof-function"></a><a name="remquof"></a>remquof 函式  
 計算第一個指定的引數除以第二個指定的引數的其餘部分。 同時計算第一個指定的引數除以第二個指定之引數的有效數字的有效數字的商數，並傳回商數使用第三個引數中指定的位置。  
  
```  
inline float remquof(
    float _X,  
    float _Y,  
    _Out_ int* _Quo) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 第一個的浮點引數。  
  
 `_Y`  
 第二個浮點引數。  
  
 `_Quo`(out 參數）  
 用來傳回小數的位元的商數的整數的位址`_X`除以小數的位元的`_Y`。  
  
### <a name="return-value"></a>傳回值  
 傳回的其餘部分`_X`除以`_Y`。  
  
##  <a name="a-namerounda--round-function"></a><a name="round"></a>round 函式  
 四捨五入至最接近整數的 _X  
  
```  
inline float round(float _X) restrict(amp);

 
inline double round(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回最接近的整數的 _X  
  
##  <a name="a-nameroundfa--roundf-function"></a><a name="roundf"></a>roundf 函式  
 四捨五入至最接近整數的 _X  
  
```  
inline float roundf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回最接近的整數的 _X  
  
##  <a name="a-namersqrta--rsqrt-function"></a><a name="rsqrt"></a>rsqrt 函式  
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
  
##  <a name="a-namersqrtfa--rsqrtf-function"></a><a name="rsqrtf"></a>rsqrtf 函式  
 傳回對等的引數的平方根  
  
```  
inline float rsqrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回對等的引數的平方根  
  
##  <a name="a-namescalba--scalb-function"></a><a name="scalb"></a>scalb 函式  
 將電源 _Y 到由 FLT_RADIX _X  
  
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
 傳回 _X * (FLT_RADIX ^ _Y)  
  
##  <a name="a-namescalbfa--scalbf-function"></a><a name="scalbf"></a>scalbf 函式  
 將電源 _Y 到由 FLT_RADIX _X  
  
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
 傳回 _X * (FLT_RADIX ^ _Y)  
  
##  <a name="a-namescalbna--scalbn-function"></a><a name="scalbn"></a>scalbn 函式  
 將電源 _Y 到由 FLT_RADIX _X  
  
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
 傳回 _X * (FLT_RADIX ^ _Y)  
  
##  <a name="a-namescalbnfa--scalbnf-function"></a><a name="scalbnf"></a>scalbnf 函式  
 將電源 _Y 到由 FLT_RADIX _X  
  
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
 傳回 _X * (FLT_RADIX ^ _Y)  
  
##  <a name="a-namesignbita--signbit-function"></a><a name="signbit"></a>signbit 函式  
 判斷是否為負數的 _X 正負號  
  
```  
inline int signbit(float _X) restrict(amp);

 
inline int signbit(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回非零值，如果且只有 _X 的正負號為負數  
  
##  <a name="a-namesignbitfa--signbitf-function"></a><a name="signbitf"></a>signbitf 函式  
 判斷是否為負數的 _X 正負號  
  
```  
inline int signbitf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回非零值，如果且只有 _X 的正負號為負數  
  
##  <a name="a-namesina--sin-function"></a><a name="sin"></a>sin 函式  
 計算引數的正弦函數值  
  
```  
inline float sin(float _X) restrict(amp);

 
inline double sin(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的正弦函數值  
  
##  <a name="a-namesinfa--sinf-function"></a><a name="sinf"></a>sinf 函式  
 計算引數的正弦函數值  
  
```  
inline float sinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的正弦函數值  
  
##  <a name="a-namesincosa--sincos-function"></a><a name="sincos"></a>sincos 函式  
 計算正弦和餘弦值 _X  
  
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
 傳回餘弦值 _X  
  
##  <a name="a-namesincosfa--sincosf-function"></a><a name="sincosf"></a>sincosf 函式  
 計算正弦和餘弦值 _X  
  
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
 傳回餘弦值 _X  
  
##  <a name="a-namesinha--sinh-function"></a><a name="sinh"></a>sinh 函式  
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
  
##  <a name="a-namesinhfa--sinhf-function"></a><a name="sinhf"></a>sinhf 函式  
 計算引數的雙曲正弦值  
  
```  
inline float sinhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的雙曲正弦值  
  
##  <a name="a-namesinpia--sinpi-function"></a><a name="sinpi"></a>sinpi 函式  
 計算 pi 的正弦值 * _X  
  
```  
inline float sinpi(float _X) restrict(amp);

 
inline double sinpi(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 pi 的正弦值 * _X  
  
##  <a name="a-namesinpifa--sinpif-function"></a><a name="sinpif"></a>sinpif 函式  
 計算 pi 的正弦值 * _X  
  
```  
inline float sinpif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 pi 的正弦值 * _X  
  
##  <a name="a-namesqrta--sqrt-function"></a><a name="sqrt"></a>sqrt 函式  
 計算引數的 squre 根  
  
```  
inline float sqrt(float _X) restrict(amp);

 
inline double sqrt(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的 squre 根目錄  
  
##  <a name="a-namesqrtfa--sqrtf-function"></a><a name="sqrtf"></a>sqrtf 函式  
 計算引數的 squre 根  
  
```  
inline float sqrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的 squre 根目錄  
  
##  <a name="a-nametana--tan-function"></a><a name="tan"></a>tan 函式  
 計算引數的正切函數值  
  
```  
inline float tan(float _X) restrict(amp);

 
inline double tan(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回正切函數的引數的值  
  
##  <a name="a-nametanfa--tanf-function"></a><a name="tanf"></a>tanf 函式  
 計算引數的正切函數值  
  
```  
inline float tanf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回正切函數的引數的值  
  
##  <a name="a-nametanha--tanh-function"></a><a name="tanh"></a>tanh 函式  
 計算引數的雙曲正切函數值  
  
```  
inline float tanh(float _X) restrict(amp);

 
inline double tanh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的雙曲正切值  
  
##  <a name="a-nametanhfa--tanhf-function"></a><a name="tanhf"></a>tanhf 函式  
 計算引數的雙曲正切函數值  
  
```  
inline float tanhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的雙曲正切值  
  
##  <a name="a-nametanpia--tanpi-function"></a><a name="tanpi"></a>tanpi 函式  
 計算 pi 的正切函數值 * _X  
  
```  
inline float tanpi(float _X) restrict(amp);

 
inline double tanpi(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 pi 的正切函數值 * _X  
  
##  <a name="a-nametanpifa--tanpif-function"></a><a name="tanpif"></a>tanpif 函式  
 計算 pi 的正切函數值 * _X  
  
```  
inline float tanpif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 pi 的正切函數值 * _X  
  
##  <a name="a-nametgammaa--tgamma-function"></a><a name="tgamma"></a>tgamma 函式  
 計算 _X gamma 的函數  
  
```  
inline float tgamma(float _X) restrict(amp);

 
inline double tgamma(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 gamma 函數的 _X 的結果  
  
##  <a name="a-nametgammafa--tgammaf-function"></a><a name="tgammaf"></a>tgammaf 函式  
 計算 _X gamma 的函數  
  
```  
inline float tgammaf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 gamma 函數的 _X 的結果  
  
##  <a name="a-nametrunca--trunc-function"></a><a name="trunc"></a>trunc 函式  
 截斷整數部分的引數  
  
```  
inline float trunc(float _X) restrict(amp);

 
inline double trunc(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的整數部分  
  
##  <a name="a-nametruncfa--truncf-function"></a><a name="truncf"></a>truncf 函式  
 截斷整數部分的引數  
  
```  
inline float truncf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的整數部分  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency:: precise_math 命名空間](concurrency-precise-math-namespace.md)

