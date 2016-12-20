---
title: "Concurrency::precise_math 命名空間 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp_math/Concurrency::precise_math"
dev_langs: 
  - "C++"
ms.assetid: ba653308-dc28-4384-b2fd-6cd718a72f91
caps.latest.revision: 6
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Concurrency::precise_math 命名空間
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

命名空間 `precise_math` 裡的函式與 C99 相容。  各函式的單精度與雙精度版本均有包含。  例如， `acos` 為雙精度版本，而 `acosf` 為單精度版本。  這些包含單精度函式在內的函式需要加速器上的擴充雙精度支援。  您可以透過 [accelerator::supports\_double\_precision 資料成員](../Topic/accelerator::supports_double_precision%20Data%20Member.md) 來檢查您是否可以在某個特定的加速器上執行這些函式。  
  
## 語法  
  
```vb  
namespace precise_math;  
```  
  
#### 參數  
  
## Members  
  
### 功能  
  
|名稱|描述|  
|--------|--------|  
|[acos 函式](../Topic/acos%20Function.md)|多載。  計算這個引數的反餘弦函式值|  
|[acosf 函式](../Topic/acosf%20Function.md)|計算這個引數的反餘弦函式值|  
|[acosh 函式](../Topic/acosh%20Function.md)|多載。  計算這個引數的反雙曲線餘弦函式值|  
|[acoshf 函式](../Topic/acoshf%20Function.md)|計算這個引數的反雙曲線餘弦函式值|  
|[asin 函式](../Topic/asin%20Function.md)|多載。  計算引數的反正弦函式值|  
|[asinf 函式](../Topic/asinf%20Function.md)|計算引數的反正弦函式值|  
|[asinh 函式](../Topic/asinh%20Function.md)|多載。  計算引數的反雙曲正弦函式值|  
|[asinhf 函式](../Topic/asinhf%20Function.md)|計算引數的反雙曲正弦函式值|  
|[atan 函式](../Topic/atan%20Function.md)|多載。  計算這個引數的反正切函式值|  
|[atan2 函式](../Topic/atan2%20Function.md)|多載。  計算 \_Y\/\_X 的反正切函式值|  
|[atan2f 函式](../Topic/atan2f%20Function.md)|計算 \_Y\/\_X 的反正切函式值|  
|[atanf 函式](../Topic/atanf%20Function.md)|計算這個引數的反正切函式值|  
|[atanh 函式](../Topic/atanh%20Function.md)|多載。  計算引數的反雙曲線正切函式值|  
|[atanhf 函式](../Topic/atanhf%20Function.md)|計算引數的反雙曲線正切函式值|  
|[cbrt 函式](../Topic/cbrt%20Function.md)|多載。  計算這個引數的實數立方根|  
|[cbrtf 函式](../Topic/cbrtf%20Function.md)|計算這個引數的實數立方根|  
|[ceil 函式](../Topic/ceil%20Function.md)|多載。  計算引數的向上取整函式值|  
|[ceilf 函式](../Topic/ceilf%20Function.md)|計算引數的向上取整函式值|  
|[copysign 函式](../Topic/copysign%20Function.md)|多載。  產生值為 \_X 且正負號為 \_Y 的值|  
|[copysignf 函式](../Topic/copysignf%20Function.md)|產生值為 \_X 且正負號為 \_Y 的值|  
|[cos 函式](../Topic/cos%20Function.md)|多載。  計算這個引數的餘弦函式值|  
|[cosf 函式](../Topic/cosf%20Function.md)|計算這個引數的餘弦函式值|  
|[cosh 函式](../Topic/cosh%20Function.md)|多載。  計算引數的雙曲線餘弦函式值|  
|[coshf 函式](../Topic/coshf%20Function.md)|計算引數的雙曲線餘弦函式值|  
|[cospi 函式](../Topic/cospi%20Function.md)|多載。  計算 pi \* \_X 的餘弦函式值|  
|[cospif 函式](../Topic/cospif%20Function.md)|計算 pi \* \_X 的餘弦函式值|  
|[erf 函式](../Topic/erf%20Function.md)|多載。  計算 \_X 的誤差函式值|  
|[erfc 函式](../Topic/erfc%20Function.md)|多載。  計算 \_X 的互補誤差函式值|  
|[erfcf 函式](../Topic/erfcf%20Function.md)|計算 \_X 的互補誤差函式值|  
|[erfcinv 函式](../Topic/erfcinv%20Function.md)|多載。  計算的 \_X 的反互補誤差函式值|  
|[erfcinvf 函式](../Topic/erfcinvf%20Function.md)|計算的 \_X 的反互補誤差函式值|  
|[erff 函式](../Topic/erff%20Function.md)|計算 \_X 的誤差函式值|  
|[erfinv 函式](../Topic/erfinv%20Function.md)|多載。  計算 \_X 的反誤差函式值|  
|[erfinvf 函式](../Topic/erfinvf%20Function.md)|計算 \_X 的反誤差函式值|  
|[exp 函式](../Topic/exp%20Function.md)|多載。  計算引數以 e 為基底的指數函式值|  
|[exp10 函式](../Topic/exp10%20Function.md)|多載。  計算引數以 10 為底數的指數函式值|  
|[exp10f 函式](../Topic/exp10f%20Function.md)|計算引數以 10 為底數的指數函式值|  
|[exp2 函式](../Topic/exp2%20Function.md)|多載。  計算引數以2為底數的指數|  
|[exp2f 函式](../Topic/exp2f%20Function.md)|計算引數以2為底數的指數|  
|[expf 函式](../Topic/expf%20Function.md)|計算引數以 e 為基底的指數函式值|  
|[expm1 函式](../Topic/expm1%20Function.md)|多載。  計算引數以 e 為基底的指數函式值減 1 。|  
|[expm1f 函式](../Topic/expm1f%20Function.md)|計算引數以 e 為基底的指數函式值減 1 。|  
|[fabs 函式](../Topic/fabs%20Function.md)|多載。  傳回引數的絕對值|  
|[fabsf 函式](../Topic/fabsf%20Function.md)|傳回引數的絕對值|  
|[fdim 函式](../Topic/fdim%20Function.md)|多載。  判斷引數之間的正差異|  
|[fdimf 函式](../Topic/fdimf%20Function.md)|判斷引數之間的正差異|  
|[floor 函式](../Topic/floor%20Function.md)|多載。  計算引數的向下取整函式值|  
|[floorf 函式](../Topic/floorf%20Function.md)|計算引數的向下取整函式值|  
|[fma 函式](../Topic/fma%20Function.md)|多載。  計算 \(\_X \* \_Y\) \+ \_Z 並四捨五入成一個三元計算。|  
|[fmaf 函式](../Topic/fmaf%20Function.md)|計算 \(\_X \* \_Y\) \+ \_Z 並四捨五入成一個三元計算。|  
|[fmax 函式](../Topic/fmax%20Function.md)|多載。  判斷引數的最大的數字值|  
|[fmaxf 函式](../Topic/fmaxf%20Function.md)|判斷引數的最大的數字值|  
|[fmin 函式](../Topic/fmin%20Function.md)|多載。  判斷引數最小的數字值|  
|[fminf 函式](../Topic/fminf%20Function.md)|判斷引數最小的數字值|  
|[fmod 函式 \(C\+\+ AMP\)](../Topic/fmod%20Function%20\(C++%20AMP\).md)|多載。  計算 \_X\/\_Y 浮點數餘數。|  
|[fmodf 函式](../Topic/fmodf%20Function.md)|計算 \_X\/\_Y 浮點數餘數。|  
|[fpclassify 函式](../Topic/fpclassify%20Function.md)|多載。  將引數值分類為 NaN，無限，一般，低品質，零|  
|[frexp 函式](../Topic/frexp%20Function.md)|多載。  取得 \_X 的尾數和指數|  
|[frexpf 函式](../Topic/frexpf%20Function.md)|取得 \_X 的尾數和指數|  
|[hypot 函式](../Topic/hypot%20Function.md)|多載。  計算 \_X 與 \_Y 的平方和的平方根。|  
|[hypotf 函式](../Topic/hypotf%20Function.md)|計算 \_X 與 \_Y 的平方和的平方根。|  
|[ilogb 函式](../Topic/ilogb%20Function.md)|多載。  擷取 \_X 的指數值成一有號整數|  
|[ilogbf 函式](../Topic/ilogbf%20Function.md)|擷取 \_X 的指數值成一有號整數|  
|[isfinite 函式](../Topic/isfinite%20Function.md)|多載。  確定引數是否有有限值。|  
|[isinf 函式](../Topic/isinf%20Function.md)|多載。  確定引數是否為無限大|  
|[isnan 函式](../Topic/isnan%20Function.md)|多載。  判斷這個引數是否為非數|  
|[isnormal 函式](../Topic/isnormal%20Function.md)|多載。  判斷這個引數是一般的|  
|[ldexp 函式](../Topic/ldexp%20Function.md)|多載。  利用尾數和指數計算出一個實數。|  
|[ldexpf 函式](../Topic/ldexpf%20Function.md)|利用尾數和指數計算出一個實數。|  
|[lgamma 函式](../Topic/lgamma%20Function.md)|多載。  計算引數的 gamma 的絕對值的自然對數函式值|  
|[lgammaf 函式](../Topic/lgammaf%20Function.md)|計算引數的 gamma 的絕對值的自然對數函式值|  
|[log 函式](../Topic/log%20Function.md)|多載。  計算引數以 e 為基底的對數函式值|  
|[log10 函式](../Topic/log10%20Function.md)|多載。  計算引數以 10 為基底的對數函式值|  
|[log10f 函式](../Topic/log10f%20Function.md)|計算引數以 10 為基底的對數函式值|  
|[log1p 函式](../Topic/log1p%20Function.md)|多載。  計算引數加 1 ，以 e 為基底的對數函式值|  
|[log1pf 函式](../Topic/log1pf%20Function.md)|計算引數加 1 ，以 e 為基底的對數函式值|  
|[log2 函式](../Topic/log2%20Function.md)|多載。  計算引數以 2 為基底的對數函式值|  
|[log2f 函式](../Topic/log2f%20Function.md)|計算引數以 2 為基底的對數函式值|  
|[logb 函式](../Topic/logb%20Function.md)|多載。  擷取 \_X 指數，當做浮點格式的帶正負號的整數 \(Unsigned Integer\) 值。|  
|[logbf 函式](../Topic/logbf%20Function.md)|擷取 \_X 指數，當做浮點格式的帶正負號的整數 \(Unsigned Integer\) 值。|  
|[logf 函式](../Topic/logf%20Function.md)|計算引數以 e 為基底的對數函式值|  
|[modf 函式](../Topic/modf%20Function.md)|多載。  分割 \_X 至分數和整數部分中。|  
|[modff 函式](../Topic/modff%20Function.md)|分割 \_X 至分數和整數部分中。|  
|[nan 函式](../Topic/nan%20Function.md)|傳回靜默非數|  
|[nanf 函式](../Topic/nanf%20Function.md)|傳回靜默非數|  
|[nearbyint 函式](../Topic/nearbyint%20Function.md)|多載。  依目前的捨入方向將引數以浮點數值的格式捨入成一整數值|  
|[nearbyintf 函式](../Topic/nearbyintf%20Function.md)|依目前的捨入方向將引數以浮點數值的格式捨入成一整數值|  
|[nextafter 函式](../Topic/nextafter%20Function.md)|多載。  以函式的形式找出依照 \_Y 的方向，在 \_X 之後下一個可以表示的數值|  
|[nextafterf 函式](../Topic/nextafterf%20Function.md)|以函式的形式找出依照 \_Y 的方向，在 \_X 之後下一個可以表示的數值|  
|[phi 函式](../Topic/phi%20Function.md)|多載。  傳回引數的累積分布函數值。|  
|[phif 函式](../Topic/phif%20Function.md)|傳回引數的累積分布函數值。|  
|[pow 函式](../Topic/pow%20Function.md)|多載。  計算 \_X 的 \_Y 次方|  
|[powf 函式](../Topic/powf%20Function.md)|計算 \_X 的 \_Y 次方|  
|[probit 函式](../Topic/probit%20Function.md)|多載。  傳回引數的反累積分布函式值|  
|[probitf 函式](../Topic/probitf%20Function.md)|傳回引數的反累積分布函式值|  
|[rcbrt 函式](../Topic/rcbrt%20Function.md)|多載。  傳回引數的立方根的倒數|  
|[rcbrtf 函式](../Topic/rcbrtf%20Function.md)|傳回引數的立方根的倒數|  
|[remainder 函式](../Topic/remainder%20Function.md)|多載。  計算餘數: \_X REM \_Y|  
|[remainderf 函式](../Topic/remainderf%20Function.md)|計算餘數: \_X REM \_Y|  
|[remquo 函式](../Topic/remquo%20Function.md)|多載。  計算與 \_X REM \_Y 相同的餘數值。  並計算整數商數 \_X\/\_Y 的較低的 23 位元，並讓該值正負號和 \_X\/\_Y 相同。  它將此有號數值儲存在 \_Quo 所指向的整數裡。|  
|[remquof 函式](../Topic/remquof%20Function.md)|計算與 \_X REM \_Y 相同的餘數值。  並計算整數商數 \_X\/\_Y 的較低的 23 位元，並讓該值正負號和 \_X\/\_Y 相同。  它將此有號數值儲存在 \_Quo 所指向的整數裡。|  
|[round 函式](../Topic/round%20Function.md)|多載。  將 \_X 捨入至最接近的整數。|  
|[roundf 函式](../Topic/roundf%20Function.md)|將 \_X 捨入至最接近的整數。|  
|[rsqrt 函式](../Topic/rsqrt%20Function.md)|多載。  傳回引數的平方根的倒數。|  
|[rsqrtf 函式](../Topic/rsqrtf%20Function.md)|傳回引數的平方根的倒數。|  
|[scalb 函式](../Topic/scalb%20Function.md)|多載。  計算 \_X 乘以 FLT\_RADIX 的 \_Y 次方|  
|[scalbf 函式](../Topic/scalbf%20Function.md)|計算 \_X 乘以 FLT\_RADIX 的 \_Y 次方|  
|[scalbn 函式](../Topic/scalbn%20Function.md)|多載。  計算 \_X 乘以 FLT\_RADIX 的 \_Y 次方|  
|[scalbnf 函式](../Topic/scalbnf%20Function.md)|計算 \_X 乘以 FLT\_RADIX 的 \_Y 次方|  
|[signbit 函式](../Topic/signbit%20Function.md)|多載。  判斷 \_X 的符號是否為負。|  
|[signbitf 函式](../Topic/signbitf%20Function.md)|判斷 \_X 的符號是否為負。|  
|[sin 函式](../Topic/sin%20Function.md)|多載。  計算這個引數的正弦值。|  
|[sincos 函式](../Topic/sincos%20Function.md)|多載。  計算 \_X 的正弦 \(Sine\) 和餘弦函數 \(Cosine\) 值|  
|[sincosf 函式](../Topic/sincosf%20Function.md)|計算 \_X 的正弦 \(Sine\) 和餘弦函數 \(Cosine\) 值|  
|[sinf 函式](../Topic/sinf%20Function.md)|計算這個引數的正弦值。|  
|[sinh 函式](../Topic/sinh%20Function.md)|多載。  計算引數的雙曲正弦函式值|  
|[sinhf 函式](../Topic/sinhf%20Function.md)|計算引數的雙曲正弦函式值|  
|[sinpi 函式](../Topic/sinpi%20Function.md)|多載。  計算 pi \* \_X 的正弦值。|  
|[sinpif 函式](../Topic/sinpif%20Function.md)|計算 pi \* \_X 的正弦值。|  
|[sqrt 函式](../Topic/sqrt%20Function.md)|多載。  計算引數的平方根|  
|[sqrtf 函式](../Topic/sqrtf%20Function.md)|計算引數的平方根|  
|[tan 函式](../Topic/tan%20Function.md)|多載。  計算這個引數的正切值|  
|[tanf 函式](../Topic/tanf%20Function.md)|計算這個引數的正切值|  
|[tanh 函式](../Topic/tanh%20Function.md)|多載。  計算引數的雙曲正切函式值|  
|[tanhf 函式](../Topic/tanhf%20Function.md)|計算引數的雙曲正切函式值|  
|[tanpi 函式](../Topic/tanpi%20Function.md)|多載。  計算角度 pi \* \_X 的正切函式值|  
|[tanpif 函式](../Topic/tanpif%20Function.md)|計算角度 pi \* \_X 的正切函式值|  
|[tgamma 函式](../Topic/tgamma%20Function.md)|多載。  計算 \_X 的 gamma 函式值|  
|[tgammaf 函式](../Topic/tgammaf%20Function.md)|計算 \_X 的 gamma 函式值|  
|[trunc 函式](../Topic/trunc%20Function.md)|多載。  將這個引數截為整數部份|  
|[truncf 函式](../Topic/truncf%20Function.md)|將這個引數截為整數部份|  
  
## 需求  
 **標頭:** amp\_math.h  
  
 **命名空間：**並行  
  
## 請參閱  
 [Concurrency 命名空間 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)