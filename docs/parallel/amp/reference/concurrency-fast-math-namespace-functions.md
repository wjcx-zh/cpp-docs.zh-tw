---
title: "Concurrency:: fast_math 命名空間函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
ms.assetid: f5763d62-795b-4de6-a7a5-c7115f158708
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 406f92d4a13502ed784936398070f1b4a7b4eb95
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
 計算引數的反餘弦  
  
```  
inline float acos(float _X) restrict(amp);
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
  
##  <a name="asin"></a>  asin  
 計算引數的反正弦  
  
```  
inline float asin(float _X) restrict(amp);
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
  
##  <a name="atan"></a>  atan  
 計算引數的反正切  
  
```  
inline float atan(float _X) restrict(amp);
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
  
##  <a name="ceil"></a>ceil  
 計算引數的上限  
  
```  
inline float ceil(float _X) restrict(amp);
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
  
##  <a name="cos"></a>  cos  
 計算引數的餘弦  
  
```  
inline float cos(float _X) restrict(amp);
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
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的雙曲餘弦值  
  
##  <a name="exp"></a>  exp  
 計算以 e 為底數的引數的指數  
  
```  
inline float exp(float _X) restrict(amp);
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
  
##  <a name="fabs"></a>fabs  
 傳回引數的絕對值  
  
```  
inline float fabs(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 整數值  
  
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
  
##  <a name="floor"></a>floor  
 計算引數的最低限度值  
  
```  
inline float floor(float _X) restrict(amp);
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
  
##  <a name="fmax"></a>fmax  
 判斷的最大的數值引數  
  
```  
inline float max(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 整數值  
  
 `_Y`  
 整數值  
  
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
inline float min(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 整數值  
  
 `_Y`  
 整數值  
  
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
  
##  <a name="fmod"></a>fmod  
 計算 _X/平均數的浮點數餘數  
  
```  
inline float fmod(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Y`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 _X/平均數的浮點數餘數  
  
##  <a name="fmodf"></a>fmodf  
 計算 _X/平均數的浮點數餘數。  
  
```  
inline float fmodf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Y`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 _X/平均數的浮點數餘數  
  
##  <a name="frexp"></a>frexp  
 取得的尾數和指數的 _X  
  
```  
inline float frexp(
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
  
##  <a name="isfinite"></a>isfinite  
 決定是否引數的有限值  
  
```  
inline int isfinite(float _X) restrict(amp);
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
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回非零值，並僅有的引數具有 NaN 值  
  
##  <a name="ldexp"></a>ldexp  
 計算實數從尾數和指數  
  
```  
inline float ldexp(
    float _X,  
    int _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值 mentissa  
  
 `_Exp`  
 整數指數  
  
### <a name="return-value"></a>傳回值  
 傳回 _X * 2 ^ _Exp  
  
##  <a name="ldexpf"></a>ldexpf  
 計算實數從尾數和指數  
  
```  
inline float ldexpf(
    float _X,  
    int _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值 mentissa  
  
 `_Exp`  
 整數指數  
  
### <a name="return-value"></a>傳回值  
 傳回 _X * 2 ^ _Exp  
  
##  <a name="log"></a>  log  
 計算引數的基底 e 對數  
  
```  
inline float log(float _X) restrict(amp);
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
  
##  <a name="log2"></a>log2  
 計算引數的底數-2 對數  
  
```  
inline float log2(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的底數-2 對數  
  
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
 會分割成小數 _X 和整數部分。  
  
```  
inline float modf(
    float _X,  
    float* _Ip) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Ip`  
  
### <a name="return-value"></a>傳回值  
 傳回 _X 帶正負號的小數的部分  
  
##  <a name="modff"></a>modff  
 會分割成小數 _X 和整數部分。  
  
```  
inline float modff(
    float _X,  
    float* _Ip) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
 `_Ip`  
  
### <a name="return-value"></a>傳回值  
 傳回 _X 帶正負號的小數的部分  
  
##  <a name="pow"></a>  pow  
 計算 _X 的乘冪的平均數  
  
```  
inline float pow(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值，基底  
  
 `_Y`  
 浮點值、 指數  
  
### <a name="return-value"></a>傳回值  
 傳回值的乘冪的平均數 _X  
  
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
  
##  <a name="round"></a>捨入  
 四捨五入為最接近整數 _X  
  
```  
inline float round(float _X) restrict(amp);
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
  
##  <a name="signbit"></a>signbit  
 判斷是否 _X 的正負號為負數  
  
```  
inline int signbit(float _X) restrict(amp);
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
    float* _S,  
    float* _C) restrict(amp);
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
    float* _S,  
    float* _C) restrict(amp);
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
  
##  <a name="sqrt"></a>  sqrt  
 計算引數的 squre 根目錄  
  
```  
inline float sqrt(float _X) restrict(amp);
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
  
##  <a name="trunc"></a>trunc  
 截斷的整數部分的引數  
  
```  
inline float trunc(float _X) restrict(amp);
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

## <a name="requirements"></a>需求
**標頭：** amp_math.h**命名空間：** concurrency:: fast_math
  
## <a name="see-also"></a>請參閱  
 [Concurrency::fast_math 命名空間](concurrency-fast-math-namespace.md)
