---
title: "Concurrency:: fast_math 命名空間 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_math/Concurrency::fast_math
dev_langs:
- C++
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: d8a94b0911b772f4972416722757bec24a4826ed
ms.contentlocale: zh-tw
ms.lasthandoff: 03/17/2017

---
# <a name="concurrencyfastmath-namespace"></a>Concurrency::fast_math 命名空間
函式的`fast_math`命名空間具有較低的精確度，支援唯一的單精確度 (`float`)，並呼叫 DirectX 內建函式。 都有兩個版本的每個函式，例如`cos`和`cosf`。 這兩個版本，並傳回`float`，但每個呼叫相同的 DirectX 內建函式。  
  
## <a name="syntax"></a>語法  
  
```  
namespace fast_math;  
```  
  
## <a name="members"></a>Members  
  
### <a name="functions"></a>函式  
  
|名稱|說明|  
|----------|-----------------|  
|[cos](concurrency-fast-math-namespace-functions.md#cos)|計算引數的反餘弦|  
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|計算引數的反餘弦|  
|[asin](concurrency-fast-math-namespace-functions.md#asin)|計算引數的反正弦值|  
|[asinf](concurrency-fast-math-namespace-functions.md#asinf)|計算引數的反正弦值|  
|[atan](concurrency-fast-math-namespace-functions.md#atan)|計算引數的反正切|  
|[atan2](concurrency-fast-math-namespace-functions.md#atan2)|計算 _Y/_X 的反正切|  
|[atan2f](concurrency-fast-math-namespace-functions.md#atan2f)|計算 _Y/_X 的反正切|  
|[atanf](concurrency-fast-math-namespace-functions.md#atanf)|計算引數的反正切|  
|[ceil](concurrency-fast-math-namespace-functions.md#ceil)|計算引數的上限|  
|[ceilf](concurrency-fast-math-namespace-functions.md#ceilf)|計算引數的上限|  
|[cos](concurrency-fast-math-namespace-functions.md#cos)|計算引數的餘弦|  
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|計算引數的餘弦|  
|[cosh](concurrency-fast-math-namespace-functions.md#cosh)|計算引數的雙曲餘弦值|  
|[coshf](concurrency-fast-math-namespace-functions.md#coshf)|計算引數的雙曲餘弦值|  
|[exp](concurrency-fast-math-namespace-functions.md#exp)|計算以 e 為底數的引數的指數|  
|[exp2](concurrency-fast-math-namespace-functions.md#exp2)|計算引數的指數底數-2|  
|[exp2f](concurrency-fast-math-namespace-functions.md#exp2f)|計算引數的指數底數-2|  
|[expf](concurrency-fast-math-namespace-functions.md#expf)|計算以 e 為底數的引數的指數|  
|[fabs](concurrency-fast-math-namespace-functions.md#fabs)|傳回引數的絕對值|  
|[fabsf](concurrency-fast-math-namespace-functions.md#fabsf)|傳回引數的絕對值|  
|[floor](concurrency-fast-math-namespace-functions.md#floor)|計算引數的最低限度值|  
|[floorf](concurrency-fast-math-namespace-functions.md#floorf)|計算引數的最低限度值|  
|[fmax](concurrency-fast-math-namespace-functions.md#fmax)|判斷引數的最大數值|  
|[fmaxf](concurrency-fast-math-namespace-functions.md#fmaxf)|判斷引數的最大數值|  
|[fmin](concurrency-fast-math-namespace-functions.md#fmin)|判斷引數的最小數值|  
|[fminf](concurrency-fast-math-namespace-functions.md#fminf)|判斷引數的最小數值|  
|[fmod](concurrency-fast-math-namespace-functions.md#fmod)|計算 _X/_Y 浮點數餘數|  
|[fmodf](concurrency-fast-math-namespace-functions.md#fmodf)|計算 _X/_Y 浮點數餘數|  
|[frexp](concurrency-fast-math-namespace-functions.md#frexp)|取得尾數和指數 _X|  
|[frexpf](concurrency-fast-math-namespace-functions.md#frexpf)|取得尾數和指數 _X|  
|[isfinite](concurrency-fast-math-namespace-functions.md#isfinite)|決定是否引數的有限值|  
|[isinf](concurrency-fast-math-namespace-functions.md#isinf)|決定是否引數是無限值|  
|[isnan](concurrency-fast-math-namespace-functions.md#isnan)|決定是否該引數是 NaN|  
|[ldexp](concurrency-fast-math-namespace-functions.md#ldexp)|計算實數尾數和指數|  
|[ldexpf](concurrency-fast-math-namespace-functions.md#ldexpf)|計算實數尾數和指數|  
|[log](concurrency-fast-math-namespace-functions.md#log)|計算引數以 e 為底數對數|  
|[log10](concurrency-fast-math-namespace-functions.md#log10)|計算引數的基底&10; 對數|  
|[log10f](concurrency-fast-math-namespace-functions.md#log10f)|計算引數的基底&10; 對數|  
|[log2](concurrency-fast-math-namespace-functions.md#log2)|計算引數的基底&2; 對數|  
|[log2f](concurrency-fast-math-namespace-functions.md#log2f)|計算引數的基底&2; 對數|  
|[logf](concurrency-fast-math-namespace-functions.md#logf)|計算引數以 e 為底數對數|  
|[modf](concurrency-fast-math-namespace-functions.md#modf)|分割成小數 _X 和整數部分。|  
|[modff](concurrency-fast-math-namespace-functions.md#modff)|分割成小數 _X 和整數部分。|  
|[pow](concurrency-fast-math-namespace-functions.md#pow)|計算乘冪的 _Y _X|  
|[powf](concurrency-fast-math-namespace-functions.md#powf)|計算乘冪的 _Y _X|  
|[round](concurrency-fast-math-namespace-functions.md#round)|四捨五入至最接近整數的 _X|  
|[roundf](concurrency-fast-math-namespace-functions.md#roundf)|四捨五入至最接近整數的 _X|  
|[rsqrt](concurrency-fast-math-namespace-functions.md#rsqrt)|傳回對等的引數的平方根|  
|[rsqrtf](concurrency-fast-math-namespace-functions.md#rsqrtf)|傳回對等的引數的平方根|  
|[signbit](concurrency-fast-math-namespace-functions.md#signbit)|傳回引數的符號|  
|[signbitf](concurrency-fast-math-namespace-functions.md#signbitf)|傳回引數的符號|  
|[sin](concurrency-fast-math-namespace-functions.md#sin)|計算引數的正弦函數值|  
|[sincos](concurrency-fast-math-namespace-functions.md#sincos)|計算正弦和餘弦值 _X|  
|[sincosf](concurrency-fast-math-namespace-functions.md#sincosf)|計算正弦和餘弦值 _X|  
|[sinf](concurrency-fast-math-namespace-functions.md#sinf)|計算引數的正弦函數值|  
|[sinh](concurrency-fast-math-namespace-functions.md#sinh)|計算引數的雙曲正弦值|  
|[sinhf](concurrency-fast-math-namespace-functions.md#sinhf)|計算引數的雙曲正弦值|  
|[sqrt](concurrency-fast-math-namespace-functions.md#sqrt)|計算引數的平方根|  
|[sqrtf](concurrency-fast-math-namespace-functions.md#sqrtf)|計算引數的平方根|  
|[tan](concurrency-fast-math-namespace-functions.md#tan)|計算引數的正切函數值|  
|[tanf](concurrency-fast-math-namespace-functions.md#tanf)|計算引數的正切函數值|  
|[tanh](concurrency-fast-math-namespace-functions.md#tanh)|計算引數的雙曲正切函數值|  
|[tanhf](concurrency-fast-math-namespace-functions.md#tanhf)|計算引數的雙曲正切函數值|  
|[trunc](concurrency-fast-math-namespace-functions.md#trunc)|截斷整數部分的引數|  
|[truncf](concurrency-fast-math-namespace-functions.md#truncf)|截斷整數部分的引數|  

## <a name="requirements"></a>需求  
 **標頭︰** amp_math.h  
  
 **命名空間︰** concurrency:: fast_math  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

