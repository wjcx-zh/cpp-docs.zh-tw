---
title: "Concurrency:: precise_math 命名空間 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_math/Concurrency::precise_math
dev_langs:
- C++
ms.assetid: ba653308-dc28-4384-b2fd-6cd718a72f91
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: b64bd3e3702701ae2685d6688d88988dd91dc5d0
ms.lasthandoff: 02/24/2017

---
# <a name="concurrencyprecisemath-namespace"></a>Concurrency::precise_math 命名空間
函式的`precise_math`命名空間是 C99 標準。 單一精確度和雙精確度的每個函式的版本隨附。 例如，`acos`是雙精度版本和`acosf`是單精確度的版本。 這些功能，包括的單精確度函式需要加速器上擴充的雙精確度支援。 您可以使用[accelerator:: supports_double_precision 資料成員](accelerator-class.md#supports_double_precision)來判斷您可以在特定的加速器上執行這些函式。 

  
## <a name="syntax"></a>語法  
  
```cpp  
namespace precise_math;  
```  
  
#### <a name="parameters"></a>參數  
  
## <a name="members"></a>Members  
  
### <a name="functions"></a>函式  
  
|名稱|說明|  
|----------|-----------------|  
|[acos 函式](concurrency-precise-math-namespace-functions.md#acos)|多載。 計算引數的反餘弦|  
|[acosf 函式](concurrency-precise-math-namespace-functions.md#acosf)|計算引數的反餘弦|  
|[acosh 函式](concurrency-precise-math-namespace-functions.md#acosh)|多載。 計算引數的反雙曲餘弦|  
|[acoshf 函式](concurrency-precise-math-namespace-functions.md#acoshf)|計算引數的反雙曲餘弦|  
|[asin 函式](concurrency-precise-math-namespace-functions.md#asin)|多載。 計算引數的反正弦值|  
|[asinf 函式](concurrency-precise-math-namespace-functions.md#asinf)|計算引數的反正弦值|  
|[asinh 函式](concurrency-precise-math-namespace-functions.md#asinh)|多載。 計算引數的反雙曲正弦|  
|[asinhf 函式](concurrency-precise-math-namespace-functions.md#asinhf)|計算引數的反雙曲正弦|  
|[atan 函式](concurrency-precise-math-namespace-functions.md#atan)|多載。 計算引數的反正切|  
|[atan2 函式](concurrency-precise-math-namespace-functions.md#atan2)|多載。 計算 _Y/_X 的反正切|  
|[atan2f 函式](concurrency-precise-math-namespace-functions.md#atan2f)|計算 _Y/_X 的反正切|  
|[atanf 函式](concurrency-precise-math-namespace-functions.md#atanf)|計算引數的反正切|  
|[atanh 函式](concurrency-precise-math-namespace-functions.md#atanh)|多載。 計算引數的反雙曲正切|  
|[atanhf 函式](concurrency-precise-math-namespace-functions.md#atanhf)|計算引數的反雙曲正切|  
|[cbrt 函式](concurrency-precise-math-namespace-functions.md#cbrt)|多載。 計算引數的實際的立方根|  
|[cbrtf 函式](concurrency-precise-math-namespace-functions.md#cbrtf)|計算引數的實際的立方根|  
|[ceil 函式](concurrency-precise-math-namespace-functions.md#ceil)|多載。 計算引數的上限|  
|[ceilf 函式](concurrency-precise-math-namespace-functions.md#ceilf)|計算引數的上限|  
|[copysign 函式](concurrency-precise-math-namespace-functions.md#copysign)|多載。 產生與 _X 且 _Y 的正負號的值|  
|[copysignf 函式](concurrency-precise-math-namespace-functions.md#copysignf)|產生與 _X 且 _Y 的正負號的值|  
|[cos 函式](concurrency-precise-math-namespace-functions.md#cos)|多載。 計算引數的餘弦|  
|[cosf 函式](concurrency-precise-math-namespace-functions.md#cosf)|計算引數的餘弦|  
|[cosh 函式](concurrency-precise-math-namespace-functions.md#cosh)|多載。 計算引數的雙曲餘弦值|  
|[coshf 函式](concurrency-precise-math-namespace-functions.md#coshf)|計算引數的雙曲餘弦值|  
|[cospi 函式](concurrency-precise-math-namespace-functions.md#cospi)|多載。 計算 pi 的餘弦值 * _X|  
|[cospif 函式](concurrency-precise-math-namespace-functions.md#cospif)|計算 pi 的餘弦值 * _X|  
|[erf 函式](concurrency-precise-math-namespace-functions.md#erf)|多載。 計算 _X 錯誤函式|  
|[erfc 函式](concurrency-precise-math-namespace-functions.md#erfc)|多載。 計算 _X 補充錯誤函式|  
|[erfcf 函式](concurrency-precise-math-namespace-functions.md#erfcf)|計算 _X 補充錯誤函式|  
|[erfcinv 函式](concurrency-precise-math-namespace-functions.md#erfcinv)|多載。 計算 _X 反向的補充錯誤函式|  
|[erfcinvf 函式](concurrency-precise-math-namespace-functions.md#erfcinvf)|計算 _X 反向的補充錯誤函式|  
|[erff 函式](concurrency-precise-math-namespace-functions.md#erff)|計算 _X 錯誤函式|  
|[erfinv 函式](concurrency-precise-math-namespace-functions.md#erfinv)|多載。 計算 _X 反向錯誤函式|  
|[erfinvf 函式](concurrency-precise-math-namespace-functions.md#erfinvf)|計算 _X 反向錯誤函式|  
|[exp 函式](concurrency-precise-math-namespace-functions.md#exp)|多載。 計算以 e 為底數的引數的指數|  
|[exp10 函式](concurrency-precise-math-namespace-functions.md#exp10)|多載。 計算指數引數的基底為&10;|  
|[exp10f 函式](concurrency-precise-math-namespace-functions.md#exp10f)|計算指數引數的基底為&10;|  
|[exp2 函式](concurrency-precise-math-namespace-functions.md#exp2)|多載。 計算引數的指數底數-2|  
|[exp2f 函式](concurrency-precise-math-namespace-functions.md#exp2f)|計算引數的指數底數-2|  
|[expf 函式](concurrency-precise-math-namespace-functions.md#expf)|計算以 e 為底數的引數的指數|  
|[expm1 函式](concurrency-precise-math-namespace-functions.md#expm1)|多載。 計算引數以 e 為底數的指數，減 1。|  
|[expm1f 函式](concurrency-precise-math-namespace-functions.md#expm1f)|計算引數以 e 為底數的指數，減 1。|  
|[fabs 函式](concurrency-precise-math-namespace-functions.md#fabs)|多載。 傳回引數的絕對值|  
|[fabsf 函式](concurrency-precise-math-namespace-functions.md#fabsf)|傳回引數的絕對值|  
|[fdim 函式](concurrency-precise-math-namespace-functions.md#fdim)|多載。 決定在引數之間的正數差異|  
|[fdimf 函式](concurrency-precise-math-namespace-functions.md#fdimf)|決定在引數之間的正數差異|  
|[floor 函式](concurrency-precise-math-namespace-functions.md#floor)|多載。 計算引數的最低限度值|  
|[floorf 函式](concurrency-precise-math-namespace-functions.md#floorf)|計算引數的最低限度值|  
|[fma 函式](concurrency-precise-math-namespace-functions.md#fma)|多載。 計算 (_X * _Y) + _Z，捨入為一個三元作業|  
|[fmaf 函式](concurrency-precise-math-namespace-functions.md#fmaf)|計算 (_X * _Y) + _Z，捨入為一個三元作業|  
|[fmax 函式](concurrency-precise-math-namespace-functions.md#fmax)|多載。 判斷引數的最大數值|  
|[fmaxf 函式](concurrency-precise-math-namespace-functions.md#fmaxf)|判斷引數的最大數值|  
|[fmin 函式](concurrency-precise-math-namespace-functions.md#fmin)|多載。 判斷引數的最小數值|  
|[fminf 函式](concurrency-precise-math-namespace-functions.md#fminf)|判斷引數的最小數值|  
|[fmod 函式 (c + + AMP)](concurrency-precise-math-namespace-functions.md#fmod)|多載。 計算 _X/_Y 浮點數餘數|  
|[fmodf 函式](concurrency-precise-math-namespace-functions.md#fmodf)|計算 _X/_Y 浮點數餘數|  
|[fpclassify 函式](concurrency-precise-math-namespace-functions.md#fpclassify)|多載。 將引數值分類為 NaN、 無限，normal subnormal，零|  
|[frexp 函式](concurrency-precise-math-namespace-functions.md#frexp)|多載。 取得尾數和指數 _X|  
|[frexpf 函式](concurrency-precise-math-namespace-functions.md#frexpf)|取得尾數和指數 _X|  
|[hypot 函式](concurrency-precise-math-namespace-functions.md#hypot)|多載。 計算的 _X 和 _Y 平方總和的平方根|  
|[hypotf 函式](concurrency-precise-math-namespace-functions.md#hypotf)|計算的 _X 和 _Y 平方總和的平方根|  
|[ilogb 函式](concurrency-precise-math-namespace-functions.md#ilogb)|多載。 擷取 _X 指數為帶正負號的 int 值|  
|[ilogbf 函式](concurrency-precise-math-namespace-functions.md#ilogbf)|擷取 _X 指數為帶正負號的 int 值|  
|[isfinite 函式](concurrency-precise-math-namespace-functions.md#isfinite)|多載。 決定是否引數的有限值|  
|[isinf 函式](concurrency-precise-math-namespace-functions.md#isinf)|多載。 決定是否引數是無限值|  
|[isnan 函式](concurrency-precise-math-namespace-functions.md#isnan)|多載。 決定是否該引數是 NaN|  
|[isnormal 函式](concurrency-precise-math-namespace-functions.md#isnormal)|多載。 判斷引數是否為標準模式|  
|[ldexp 函式](concurrency-precise-math-namespace-functions.md#ldexp)|多載。 計算實數尾數和指數|  
|[ldexpf 函式](concurrency-precise-math-namespace-functions.md#ldexpf)|計算實數尾數和指數|  
|[lgamma 函式](concurrency-precise-math-namespace-functions.md#lgamma)|多載。 計算自然對數的 gamma 引數的絕對值|  
|[lgammaf 函式](concurrency-precise-math-namespace-functions.md#lgammaf)|計算自然對數的 gamma 引數的絕對值|  
|[log 函式](concurrency-precise-math-namespace-functions.md#log)|多載。 計算引數以 e 為底數對數|  
|[log10 函式](concurrency-precise-math-namespace-functions.md#log10)|多載。 計算引數的基底&10; 對數|  
|[log10f 函式](concurrency-precise-math-namespace-functions.md#log10f)|計算引數的基底&10; 對數|  
|[log1p 函式](concurrency-precise-math-namespace-functions.md#log1p)|多載。 計算以 e 為底數的對數 1 再加上引數|  
|[log1pf 函式](concurrency-precise-math-namespace-functions.md#log1pf)|計算以 e 為底數的對數 1 再加上引數|  
|[log2 函式](concurrency-precise-math-namespace-functions.md#log2)|多載。 計算引數的基底&2; 對數|  
|[log2f 函式](concurrency-precise-math-namespace-functions.md#log2f)|計算引數的基底&2; 對數|  
|[logb 函式](concurrency-precise-math-namespace-functions.md#logb)|多載。 擷取 _X，指數為帶正負號的整數中的值的浮點格式|  
|[logbf 函式](concurrency-precise-math-namespace-functions.md#logbf)|擷取 _X，指數為帶正負號的整數中的值的浮點格式|  
|[logf 函式](concurrency-precise-math-namespace-functions.md#logf)|計算引數以 e 為底數對數|  
|[modf 函式](concurrency-precise-math-namespace-functions.md#modf)|多載。 分割成小數 _X 和整數部分。|  
|[modff 函式](concurrency-precise-math-namespace-functions.md#modff)|分割成小數 _X 和整數部分。|  
|[nan 函式](concurrency-precise-math-namespace-functions.md#nan)|傳回無訊息 NaN|  
|[nanf 函式](concurrency-precise-math-namespace-functions.md#nanf)|傳回無訊息 NaN|  
|[nearbyint 函式](concurrency-precise-math-namespace-functions.md#nearbyint)|多載。 四捨五入至浮點格式，使用目前的捨入方向的整數值的引數。|  
|[nearbyintf 函式](concurrency-precise-math-namespace-functions.md#nearbyintf)|四捨五入至浮點格式，使用目前的捨入方向的整數值的引數。|  
|[nextafter 函式](concurrency-precise-math-namespace-functions.md#nextafter)|多載。 判斷 _X _Y 的方向之後的下一個可顯示值，函數的類型|  
|[nextafterf 函式](concurrency-precise-math-namespace-functions.md#nextafterf)|判斷 _X _Y 的方向之後的下一個可顯示值，函數的類型|  
|[phi 函式](concurrency-precise-math-namespace-functions.md#phi)|多載。 傳回累加分配函數的引數|  
|[phif 函式](concurrency-precise-math-namespace-functions.md#phif)|傳回累加分配函數的引數|  
|[pow 函式](concurrency-precise-math-namespace-functions.md#pow)|多載。 計算乘冪的 _Y _X|  
|[powf 函式](concurrency-precise-math-namespace-functions.md#powf)|計算乘冪的 _Y _X|  
|[probit 函式](concurrency-precise-math-namespace-functions.md#probit)|多載。 傳回反向累積分佈函數的引數|  
|[probitf 函式](concurrency-precise-math-namespace-functions.md#probitf)|傳回反向累積分佈函數的引數|  
|[rcbrt 函式](concurrency-precise-math-namespace-functions.md#rcbrt)|多載。 傳回對等的引數的立方根|  
|[rcbrtf 函式](concurrency-precise-math-namespace-functions.md#rcbrtf)|傳回對等的引數的立方根|  
|[remainder 函式](concurrency-precise-math-namespace-functions.md#remainder)|多載。 計算餘數︰ _X REM _Y|  
|[remainderf 函式](concurrency-precise-math-namespace-functions.md#remainderf)|計算餘數︰ _X REM _Y|  
|[remquo 函式](concurrency-precise-math-namespace-functions.md#remquo)|多載。 會計算為 _X REM _Y 相同的餘數。 也會計算較低的 23 位元的整數商數 _X/_Y，並提供相同的簽章，為 _X/_Y 該值。 _Quo 所指的整數，它就會儲存此帶正負號的值。|  
|[remquof 函式](concurrency-precise-math-namespace-functions.md#remquof)|會計算為 _X REM _Y 相同的餘數。 也會計算較低的 23 位元的整數商數 _X/_Y，並提供相同的簽章，為 _X/_Y 該值。 _Quo 所指的整數，它就會儲存此帶正負號的值。|  
|[round 函式](concurrency-precise-math-namespace-functions.md#round)|多載。 四捨五入至最接近整數的 _X|  
|[roundf 函式](concurrency-precise-math-namespace-functions.md#roundf)|四捨五入至最接近整數的 _X|  
|[rsqrt 函式](concurrency-precise-math-namespace-functions.md#rsqrt)|多載。 傳回對等的引數的平方根|  
|[rsqrtf 函式](concurrency-precise-math-namespace-functions.md#rsqrtf)|傳回對等的引數的平方根|  
|[scalb 函式](concurrency-precise-math-namespace-functions.md#scalb)|多載。 將電源 _Y 到由 FLT_RADIX _X|  
|[scalbf 函式](concurrency-precise-math-namespace-functions.md#scalbf)|將電源 _Y 到由 FLT_RADIX _X|  
|[scalbn 函式](concurrency-precise-math-namespace-functions.md#scalbn)|多載。 將電源 _Y 到由 FLT_RADIX _X|  
|[scalbnf 函式](concurrency-precise-math-namespace-functions.md#scalbnf)|將電源 _Y 到由 FLT_RADIX _X|  
|[signbit 函式](concurrency-precise-math-namespace-functions.md#signbit)|多載。 判斷是否為負數的 _X 正負號|  
|[signbitf 函式](concurrency-precise-math-namespace-functions.md#signbitf)|判斷是否為負數的 _X 正負號|  
|[sin 函式](concurrency-precise-math-namespace-functions.md#sin)|多載。 計算引數的正弦函數值|  
|[sincos 函式](concurrency-precise-math-namespace-functions.md#sincos)|多載。 計算正弦和餘弦值 _X|  
|[sincosf 函式](concurrency-precise-math-namespace-functions.md#sincosf)|計算正弦和餘弦值 _X|  
|[sinf 函式](concurrency-precise-math-namespace-functions.md#sinf)|計算引數的正弦函數值|  
|[sinh 函式](concurrency-precise-math-namespace-functions.md#sinh)|多載。 計算引數的雙曲正弦值|  
|[sinhf 函式](concurrency-precise-math-namespace-functions.md#sinhf)|計算引數的雙曲正弦值|  
|[sinpi 函式](concurrency-precise-math-namespace-functions.md#sinpi)|多載。 計算 pi 的正弦值 * _X|  
|[sinpif 函式](concurrency-precise-math-namespace-functions.md#sinpif)|計算 pi 的正弦值 * _X|  
|[sqrt 函式](concurrency-precise-math-namespace-functions.md#sqrt)|多載。 計算引數的 squre 根|  
|[sqrtf 函式](concurrency-precise-math-namespace-functions.md#sqrtf)|計算引數的 squre 根|  
|[tan 函式](concurrency-precise-math-namespace-functions.md#tan)|多載。 計算引數的正切函數值|  
|[tanf 函式](concurrency-precise-math-namespace-functions.md#tanf)|計算引數的正切函數值|  
|[tanh 函式](concurrency-precise-math-namespace-functions.md#tanh)|多載。 計算引數的雙曲正切函數值|  
|[tanhf 函式](concurrency-precise-math-namespace-functions.md#tanhf)|計算引數的雙曲正切函數值|  
|[tanpi 函式](concurrency-precise-math-namespace-functions.md#tanpi)|多載。 計算 pi 的正切函數值 * _X|  
|[tanpif 函式](concurrency-precise-math-namespace-functions.md#tanpif)|計算 pi 的正切函數值 * _X|  
|[tgamma 函式](concurrency-precise-math-namespace-functions.md#tgamma)|多載。 計算 _X gamma 的函數|  
|[tgammaf 函式](concurrency-precise-math-namespace-functions.md#tgammaf)|計算 _X gamma 的函數|  
|[trunc 函式](concurrency-precise-math-namespace-functions.md#trunc)|多載。 截斷整數部分的引數|  
|[truncf 函式](concurrency-precise-math-namespace-functions.md#truncf)|截斷整數部分的引數|  
  
## <a name="requirements"></a>需求  
 **標頭︰** amp_math.h  
  
 **命名空間：** 並行  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (c + + AMP)](concurrency-namespace-cpp-amp.md)

