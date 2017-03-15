---
title: "Concurrency:: fast_math 命名空間函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5763d62-795b-4de6-a7a5-c7115f158708
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 4a01f48a7d087281ab1e9222d1077e92ab8b0d6c
ms.openlocfilehash: 0545a57c492f5c1872c71c04c99b54f86b644102
ms.lasthandoff: 02/24/2017

---
# <a name="concurrencyfastmath-namespace-functions"></a>Concurrency:: fast_math 命名空間函式
||||  
|-|-|-|  
|[acos 函式](#acos)|[acosf 函式](#acosf)|[asin 函式](#asin)|  
|[asinf 函式](#asinf)|[atan 函式](#atan)|[atan2 函式](#atan2)|  
|[atan2f 函式](#atan2f)|[atanf 函式](#atanf)|[ceil 函式](#ceil)|  
|[ceilf 函式](#ceilf)|[cos 函式](#cos)|[cosf 函式](#cosf)|  
|[cosh 函式](#cosh)|[coshf 函式](#coshf)|[exp 函式](#exp)|  
|[exp2 函式](#exp2)|[exp2f 函式](#exp2f)|[expf 函式](#expf)|  
|[fabs 函式](#fabs)|[fabsf 函式](#fabsf)|[floor 函式](#floor)|  
|[floorf 函式](#floorf)|[fmax 函式](#fmax)|[fmaxf 函式](#fmaxf)|  
|[fmin 函式](#fmin)|[fminf 函式](#fminf)|[fmod 函式](#fmod)|  
|[fmodf 函式](#fmodf)|[frexp 函式](#frexp)|[frexpf 函式](#frexpf)|  
|[isfinite 函式](#isfinite)|[isinf 函式](#isinf)|[isnan 函式](#isnan)|  
|[ldexp 函式](#ldexp)|[ldexpf 函式](#ldexpf)|[log 函式](#log)|  
|[log10 函式](#log10)|[log10f 函式](#log10f)|[log2 函式](#log2)|  
|[log2f 函式](#log2f)|[logf 函式](#logf)|[modf 函式](#modf)|  
|[modff 函式](#modff)|[pow 函式](#pow)|[powf 函式](#powf)|  
|[round 函式](#round)|[roundf 函式](#roundf)|[rsqrt 函式](#rsqrt)|  
|[rsqrtf 函式](#rsqrtf)|[signbit 函式](#signbit)|[signbitf 函式](#signbitf)|  
|[sin 函式](#sin)|[sincos 函式](#sincos)|[sincosf 函式](#sincosf)|  
|[sinf 函式](#sinf)|[sinh 函式](#sinh)|[sinhf 函式](#sinhf)|  
|[sqrt 函式](#sqrt)|[sqrtf 函式](#sqrtf)|[tan 函式](#tan)|  
|[tanf 函式](#tanf)|[tanh 函式](#tanh)|[tanhf 函式](#tanhf)|  
|[trunc 函式](#trunc)|[truncf 函式](#truncf)|  
  
##  <a name="a-nameacosa--acos-function"></a><a name="acos"></a>acos 函式  
 計算引數的反餘弦  
  
```  
inline float acos(float _X) restrict(amp);
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
  
##  <a name="a-nameasina--asin-function"></a><a name="asin"></a>asin 函式  
 計算引數的反正弦值  
  
```  
inline float asin(float _X) restrict(amp);
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
  
##  <a name="a-nameatana--atan-function"></a><a name="atan"></a>atan 函式  
 計算引數的反正切  
  
```  
inline float atan(float _X) restrict(amp);
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
  
##  <a name="a-nameceila--ceil-function"></a><a name="ceil"></a>ceil 函式  
 計算引數的上限  
  
```  
inline float ceil(float _X) restrict(amp);
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
  
##  <a name="a-namecosa--cos-function"></a><a name="cos"></a>cos 函式   
 計算引數的餘弦  
  
```  
inline float cos(float _X) restrict(amp);
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
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的雙曲餘弦值  
  
##  <a name="a-nameexpa--exp-function"></a><a name="exp"></a>exp 函式  
 計算以 e 為底數的引數的指數  
  
```  
inline float exp(float _X) restrict(amp);
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
  
##  <a name="a-namefabsa--fabs-function"></a><a name="fabs"></a>fabs 函式  
 傳回引數的絕對值  
  
```  
inline float fabs(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 整數值  
  
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
  
##  <a name="a-namefloora--floor-function"></a><a name="floor"></a>floor 函式  
 計算引數的最低限度值  
  
```  
inline float floor(float _X) restrict(amp);
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
  
##  <a name="a-namefmaxa--fmax-function"></a><a name="fmax"></a>fmax 函式  
 判斷引數的最大數值  
  
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
  
##  <a name="a-namefmoda--fmod-function"></a><a name="fmod"></a>fmod 函式  
 計算 _X/_Y 浮點數餘數  
  
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
 傳回 _X/_Y 浮點數餘數  
  
##  <a name="a-namefmodfa--fmodf-function"></a><a name="fmodf"></a>fmodf 函式  
 計算 _X/_Y 浮點數餘數。  
  
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
 傳回 _X/_Y 浮點數餘數  
  
##  <a name="a-namefrexpa--frexp-function"></a><a name="frexp"></a>frexp 函式  
 取得尾數和指數 _X  
  
```  
inline float frexp(
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
  
##  <a name="a-nameisfinitea--isfinite-function"></a><a name="isfinite"></a>isfinite 函式  
 決定是否引數的有限值  
  
```  
inline int isfinite(float _X) restrict(amp);
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
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回非零值，如果且只有引數的 NaN 值  
  
##  <a name="a-nameldexpa--ldexp-function"></a><a name="ldexp"></a>ldexp 函式  
 計算實數尾數和指數  
  
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
  
##  <a name="a-nameldexpfa--ldexpf-function"></a><a name="ldexpf"></a>ldexpf 函式  
 計算實數尾數和指數  
  
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
  
##  <a name="a-nameloga--log-function"></a><a name="log"></a>log 函式  
 計算引數以 e 為底數對數  
  
```  
inline float log(float _X) restrict(amp);
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
  
##  <a name="a-namelog2a--log2-function"></a><a name="log2"></a>log2 函式  
 計算引數的基底&2; 對數  
  
```  
inline float log2(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回引數的基底&2; 對數  
  
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
 分割成小數 _X 和整數部分。  
  
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
 傳回的帶正負號的小數部分的 _X  
  
##  <a name="a-namemodffa--modff-function"></a><a name="modff"></a>modff 函式  
 分割成小數 _X 和整數部分。  
  
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
 傳回的帶正負號的小數部分的 _X  
  
##  <a name="a-namepowa--pow-function"></a><a name="pow"></a>pow 函式  
 計算乘冪的 _Y _X  
  
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
 傳回 _X _Y 的乘冪數的值  
  
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
  
##  <a name="a-namerounda--round-function"></a><a name="round"></a>round 函式  
 四捨五入至最接近整數的 _X  
  
```  
inline float round(float _X) restrict(amp);
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
  
##  <a name="a-namesignbita--signbit-function"></a><a name="signbit"></a>signbit 函式  
 判斷是否為負數的 _X 正負號  
  
```  
inline int signbit(float _X) restrict(amp);
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
    float* _S,  
    float* _C) restrict(amp);
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
    float* _S,  
    float* _C) restrict(amp);
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
  
##  <a name="a-namesqrta--sqrt-function"></a><a name="sqrt"></a>sqrt 函式  
 計算引數的 squre 根  
  
```  
inline float sqrt(float _X) restrict(amp);
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
  
##  <a name="a-nametrunca--trunc-function"></a><a name="trunc"></a>trunc 函式  
 截斷整數部分的引數  
  
```  
inline float trunc(float _X) restrict(amp);
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
 [Concurrency:: fast_math 命名空間](concurrency-fast-math-namespace.md)

