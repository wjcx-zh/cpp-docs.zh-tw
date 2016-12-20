---
title: "Concurrency::fast_math 命名空間 | Microsoft Docs"
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
  - "amp_math/Concurrency::fast_math"
dev_langs: 
  - "C++"
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
caps.latest.revision: 9
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Concurrency::fast_math 命名空間
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`fast_math` 命名空間中的函式具有較低精確度，僅支援單精確度 \(`float`\)，並呼叫 DirectX 內建。  每個函式有兩種版本，例如 `cos` 和 `cosf`。  兩個版本都會接受並傳回 `float`，但各自呼叫相同的 DirectX 內建。  
  
## 語法  
  
```  
namespace fast_math;  
```  
  
## Members  
  
### 功能  
  
|名稱|描述|  
|--------|--------|  
|[cos 函式 \(fast\_math\)](../Topic/cos%20Function%20%20\(fast_math\).md)|計算引數的反餘弦函數 \(Arccosine\) 值|  
|[cosf 函式 \(fast\_math\)](../Topic/cosf%20Function%20\(fast_math\).md)|計算引數的反餘弦函數 \(Arccosine\) 值|  
|[asin 函式 \(fast\_math\)](../Topic/asin%20Function%20\(fast_math\).md)|計算引數的反正弦函數 \(Arcsine\) 值|  
|[asinf 函式 \(fast\_math\)](../Topic/asinf%20Function%20\(fast_math\).md)|計算引數的反正弦函數 \(Arcsine\) 值|  
|[atan 函式 \(fast\_math\)](../Topic/atan%20Function%20\(fast_math\).md)|計算引數的反正切函數 \(Arctangent\) 值|  
|[atan2 函式 \(fast\_math\)](../Topic/atan2%20Function%20\(fast_math\).md)|計算 \_Y\/\_X 的反正切函數 \(Arctangent\) 值|  
|[atan2f 函式 \(fast\_math\)](../Topic/atan2f%20Function%20\(fast_math\).md)|計算 \_Y\/\_X 的反正切函數 \(Arctangent\) 值|  
|[atanf 函式 \(fast\_math\)](../Topic/atanf%20Function%20\(fast_math\).md)|計算引數的反正切函數 \(Arctangent\) 值|  
|[ceil 函式 \(fast\_math\)](../Topic/ceil%20Function%20\(fast_math\).md)|計算引數的向上取整函數值|  
|[ceilf 函式 \(fast\_math\)](../Topic/ceilf%20Function%20\(fast_math\).md)|計算引數的向上取整函數值|  
|[cos 函式 \(fast\_math\)](../Topic/cos%20Function%20%20\(fast_math\).md)|計算引數的餘弦函數 \(Cosine\) 值|  
|[cosf 函式 \(fast\_math\)](../Topic/cosf%20Function%20\(fast_math\).md)|計算引數的餘弦函數 \(Cosine\) 值|  
|[cosh 函式 \(fast\_math\)](../Topic/cosh%20Function%20\(fast_math\).md)|計算引數的雙曲線餘弦函數 \(Hyperbolic Cosine\) 值|  
|[coshf 函式 \(fast\_math\)](../Topic/coshf%20Function%20\(fast_math\).md)|計算引數的雙曲線餘弦函數 \(Hyperbolic Cosine\) 值|  
|[exp 函式 \(fast\_math\)](../Topic/exp%20Function%20\(fast_math\).md)|計算引數以 e 為基底的指數函數值|  
|[exp2 函式 \(fast\_math\)](../Topic/exp2%20Function%20\(fast_math\).md)|計算引數以 2 為底數的指數|  
|[exp2f 函式 \(fast\_math\)](../Topic/exp2f%20Function%20\(fast_math\).md)|計算引數以 2 為底數的指數|  
|[expf 函式 \(fast\_math\)](../Topic/expf%20Function%20\(fast_math\).md)|計算引數以 e 為基底的指數函數值|  
|[fabs 函式 \(fast\_math\)](../Topic/fabs%20Function%20\(fast_math\).md)|傳回引數的絕對值|  
|[fabsf 函式 \(fast\_math\)](../Topic/fabsf%20Function%20\(fast_math\).md)|傳回引數的絕對值|  
|[floor 函式 \(fast\_math\)](../Topic/floor%20Function%20\(fast_math\).md)|計算引數的向下取整函數值|  
|[floorf 函式 \(fast\_math\)](../Topic/floorf%20Function%20\(fast_math\).md)|計算引數的向下取整函數值|  
|[fmax 函式 \(fast\_math\)](../Topic/fmax%20Function%20\(fast_math\).md)|判斷引數的最大數值|  
|[fmaxf 函式 \(fast\_math\)](../Topic/fmaxf%20Function%20\(fast_math\).md)|判斷引數的最大數值|  
|[fmin 函式 \(fast\_math\)](../Topic/fmin%20Function%20\(fast_math\).md)|判斷引數的最小數值|  
|[fminf 函式 \(fast\_math\)](../Topic/fminf%20Function%20\(fast_math\).md)|判斷引數的最小數值|  
|[fmod 函式 \(fast\_math\)](../Topic/fmod%20Function%20\(fast_math\).md)|計算 \_X\/\_Y 浮點數餘數。|  
|[fmodf 函式 \(fast\_math\)](../Topic/fmodf%20Function%20\(fast_math\).md)|計算 \_X\/\_Y 浮點數餘數。|  
|[frexp 函式 \(fast\_math\)](../Topic/frexp%20Function%20\(fast_math\).md)|取得 \_X 的尾數和指數|  
|[frexpf 函式 \(fast\_math\)](../Topic/frexpf%20Function%20\(fast_math\).md)|取得 \_X 的尾數和指數|  
|[isfinite 函式 \(fast\_math\)](../Topic/isfinite%20Function%20\(fast_math\).md)|判斷引數值是否為有限值。|  
|[isinf 函式 \(fast\_math\)](../Topic/isinf%20Function%20\(fast_math\).md)|判斷引數是否為無限大|  
|[isnan 函式 \(fast\_math\)](../Topic/isnan%20Function%20\(fast_math\).md)|判斷引數是否為 NaN|  
|[ldexp 函式 \(fast\_math\)](../Topic/ldexp%20Function%20\(fast_math\).md)|利用尾數和指數計算出實數|  
|[ldexpf 函式 \(fast\_math\)](../Topic/ldexpf%20Function%20\(fast_math\).md)|利用尾數和指數計算出實數|  
|[log 函式 \(fast\_math\)](../Topic/log%20Function%20\(fast_math\).md)|計算引數以 e 為基底的對數函數值|  
|[log10 函式 \(fast\_math\)](../Topic/log10%20Function%20\(fast_math\).md)|計算引數以 10 為基底的對數函式值|  
|[log10f 函式 \(fast\_math\)](../Topic/log10f%20Function%20\(fast_math\).md)|計算引數以 10 為基底的對數函式值|  
|[log2 函式 \(fast\_math\)](../Topic/log2%20Function%20\(fast_math\).md)|計算引數以 2 為基底的對數函數值|  
|[log2f 函式 \(fast\_math\)](../Topic/log2f%20Function%20\(fast_math\).md)|計算引數以 2 為基底的對數函數值|  
|[logf 函式 \(fast\_math\)](../Topic/logf%20Function%20\(fast_math\).md)|計算引數以 e 為基底的對數函數值|  
|[modf 函式 \(fast\_math\)](../Topic/modf%20Function%20\(fast_math\).md)|將 \_X 分割為分數和整數部分。|  
|[modff 函式 \(fast\_math\)](../Topic/modff%20Function%20\(fast_math\).md)|將 \_X 分割為分數和整數部分。|  
|[pow 函式 \(fast\_math\)](../Topic/pow%20Function%20\(fast_math\).md)|計算 \_X 的 \_Y 次方|  
|[powf 函式 \(fast\_math\)](../Topic/powf%20Function%20\(fast_math\).md)|計算 \_X 的 \_Y 次方|  
|[round 函式 \(fast\_math\)](../Topic/round%20Function%20\(fast_math\).md)|將 \_X 捨入至最接近的整數|  
|[roundf 函式 \(fast\_math\)](../Topic/roundf%20Function%20\(fast_math\).md)|將 \_X 捨入至最接近的整數|  
|[rsqrt 函式 \(fast\_math\)](../Topic/rsqrt%20Function%20\(fast_math\).md)|傳回引數平方根的倒數|  
|[rsqrtf 函式 \(fast\_math\)](../Topic/rsqrtf%20Function%20\(fast_math\).md)|傳回引數平方根的倒數|  
|[signbit 函式 \(fast\_math\)](../Topic/signbit%20Function%20\(fast_math\).md)|傳回引數的正負號|  
|[signbitf 函式 \(fast\_math\)](../Topic/signbitf%20Function%20\(fast_math\).md)|傳回引數的正負號|  
|[sin 函式 \(fast\_math\)](../Topic/sin%20Function%20\(fast_math\).md)|計算這個引數的正函數 \(Sine\) 值。|  
|[sincos 函式 \(fast\_math\)](../Topic/sincos%20Function%20\(fast_math\).md)|計算 \_X 的正弦 \(Sine\) 和餘弦函數 \(Cosine\) 值|  
|[sincosf 函式 \(fast\_math\)](../Topic/sincosf%20Function%20\(fast_math\).md)|計算 \_X 的正弦 \(Sine\) 和餘弦函數 \(Cosine\) 值|  
|[sinf 函式 \(fast\_math\)](../Topic/sinf%20Function%20\(fast_math\).md)|計算這個引數的正函數 \(Sine\) 值。|  
|[sinh 函式 \(fast\_math\)](../Topic/sinh%20Function%20\(fast_math\).md)|計算引數的雙曲正弦函數 \(Hyperbolic Sine\) 值|  
|[sinhf 函式 \(fast\_math\)](../Topic/sinhf%20Function%20\(fast_math\).md)|計算引數的雙曲正弦函數 \(Hyperbolic Sine\) 值|  
|[sqrt 函式 \(fast\_math\)](../Topic/sqrt%20Function%20\(fast_math\).md)|計算引數的平方根|  
|[sqrtf 函式 \(fast\_math\)](../Topic/sqrtf%20Function%20\(fast_math\).md)|計算引數的平方根|  
|[tan 函式 \(fast\_math\)](../Topic/tan%20Function%20\(fast_math\).md)|計算引數的正切正切函數 \(Tangent\) 值|  
|[tanf 函式 \(fast\_math\)](../Topic/tanf%20Function%20\(fast_math\).md)|計算引數的正切正切函數 \(Tangent\) 值|  
|[tanh 函式 \(fast\_math\)](../Topic/tanh%20Function%20\(fast_math\).md)|計算引數的雙曲正切函數 \(Hyperbolic Tangent\) 值|  
|[tanhf 函式 \(fast\_math\)](../Topic/tanhf%20Function%20\(fast_math\).md)|計算引數的雙曲正切函數 \(Hyperbolic Tangent\) 值|  
|[trunc 函式 \(fast\_math\)](../Topic/trunc%20Function%20\(fast_math\).md)|將引數截為整數部分|  
|[truncf 函式 \(fast\_math\)](../Topic/truncf%20Function%20\(fast_math\).md)|將引數截為整數部分|  
  
## 需求  
 **標頭：**amp\_math.h  
  
 **命名空間：**Concurrency::fast\_math  
  
## 請參閱  
 [Concurrency 命名空間 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)