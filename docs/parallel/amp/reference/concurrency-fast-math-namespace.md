---
title: 'Concurrency:: fast_math 命名空間 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- amp_math/Concurrency::fast_math
dev_langs:
- C++
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04a9cd3d604b18e42202bccb287cce7c7416b51f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="concurrencyfastmath-namespace"></a>Concurrency::fast_math 命名空間
中的函式`fast_math`命名空間包含降低精確度，支援唯一的單精確度 (`float`)，並呼叫 DirectX 內建函式。 兩種版本的每個函式，例如`cos`和`cosf`。 這兩個版本，並傳回`float`，但每個呼叫相同的 DirectX 內建函式。  
  
## <a name="syntax"></a>語法  
  
```  
namespace fast_math;  
```  
  
## <a name="members"></a>成員  
  
### <a name="functions"></a>函式  
  
|名稱|描述|  
|----------|-----------------|  
|[cos](concurrency-fast-math-namespace-functions.md#cos)|計算引數的反餘弦|  
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|計算引數的反餘弦|  
|[asin](concurrency-fast-math-namespace-functions.md#asin)|計算引數的反正弦|  
|[asinf](concurrency-fast-math-namespace-functions.md#asinf)|計算引數的反正弦|  
|[atan](concurrency-fast-math-namespace-functions.md#atan)|計算引數的反正切|  
|[atan2](concurrency-fast-math-namespace-functions.md#atan2)|計算反正切平均數/_X|  
|[atan2f](concurrency-fast-math-namespace-functions.md#atan2f)|計算反正切平均數/_X|  
|[atanf](concurrency-fast-math-namespace-functions.md#atanf)|計算引數的反正切|  
|[ceil](concurrency-fast-math-namespace-functions.md#ceil)|計算引數的上限|  
|[ceilf](concurrency-fast-math-namespace-functions.md#ceilf)|計算引數的上限|  
|[cos](concurrency-fast-math-namespace-functions.md#cos)|計算引數的餘弦|  
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|計算引數的餘弦|  
|[cosh](concurrency-fast-math-namespace-functions.md#cosh)|計算引數的雙曲餘弦值|  
|[coshf](concurrency-fast-math-namespace-functions.md#coshf)|計算引數的雙曲餘弦值|  
|[exp](concurrency-fast-math-namespace-functions.md#exp)|計算以 e 為底數的引數的指數|  
|[exp2](concurrency-fast-math-namespace-functions.md#exp2)|計算基底 2 指數的引數|  
|[exp2f](concurrency-fast-math-namespace-functions.md#exp2f)|計算基底 2 指數的引數|  
|[expf](concurrency-fast-math-namespace-functions.md#expf)|計算以 e 為底數的引數的指數|  
|[fabs](concurrency-fast-math-namespace-functions.md#fabs)|傳回引數的絕對值|  
|[fabsf](concurrency-fast-math-namespace-functions.md#fabsf)|傳回引數的絕對值|  
|[floor](concurrency-fast-math-namespace-functions.md#floor)|計算引數的最低限度值|  
|[floorf](concurrency-fast-math-namespace-functions.md#floorf)|計算引數的最低限度值|  
|[fmax](concurrency-fast-math-namespace-functions.md#fmax)|判斷的最大的數值引數|  
|[fmaxf](concurrency-fast-math-namespace-functions.md#fmaxf)|判斷的最大的數值引數|  
|[fmin](concurrency-fast-math-namespace-functions.md#fmin)|判斷引數的最小數值|  
|[fminf](concurrency-fast-math-namespace-functions.md#fminf)|判斷引數的最小數值|  
|[fmod](concurrency-fast-math-namespace-functions.md#fmod)|計算 _X/平均數的浮點數餘數|  
|[fmodf](concurrency-fast-math-namespace-functions.md#fmodf)|計算 _X/平均數的浮點數餘數|  
|[frexp](concurrency-fast-math-namespace-functions.md#frexp)|取得的尾數和指數的 _X|  
|[frexpf](concurrency-fast-math-namespace-functions.md#frexpf)|取得的尾數和指數的 _X|  
|[isfinite](concurrency-fast-math-namespace-functions.md#isfinite)|決定是否引數的有限值|  
|[isinf](concurrency-fast-math-namespace-functions.md#isinf)|判斷是否引數為無限|  
|[isnan](concurrency-fast-math-namespace-functions.md#isnan)|判斷引數是否為 NaN|  
|[ldexp](concurrency-fast-math-namespace-functions.md#ldexp)|計算實數從尾數和指數|  
|[ldexpf](concurrency-fast-math-namespace-functions.md#ldexpf)|計算實數從尾數和指數|  
|[log](concurrency-fast-math-namespace-functions.md#log)|計算引數的基底 e 對數|  
|[log10](concurrency-fast-math-namespace-functions.md#log10)|計算引數的基底 10 對數|  
|[log10f](concurrency-fast-math-namespace-functions.md#log10f)|計算引數的基底 10 對數|  
|[log2](concurrency-fast-math-namespace-functions.md#log2)|計算引數的底數-2 對數|  
|[log2f](concurrency-fast-math-namespace-functions.md#log2f)|計算引數的底數-2 對數|  
|[logf](concurrency-fast-math-namespace-functions.md#logf)|計算引數的基底 e 對數|  
|[modf](concurrency-fast-math-namespace-functions.md#modf)|會分割成小數 _X 和整數部分。|  
|[modff](concurrency-fast-math-namespace-functions.md#modff)|會分割成小數 _X 和整數部分。|  
|[pow](concurrency-fast-math-namespace-functions.md#pow)|計算 _X 的乘冪的平均數|  
|[powf](concurrency-fast-math-namespace-functions.md#powf)|計算 _X 的乘冪的平均數|  
|[round](concurrency-fast-math-namespace-functions.md#round)|四捨五入為最接近整數 _X|  
|[roundf](concurrency-fast-math-namespace-functions.md#roundf)|四捨五入為最接近整數 _X|  
|[rsqrt](concurrency-fast-math-namespace-functions.md#rsqrt)|傳回對等的引數的平方根|  
|[rsqrtf](concurrency-fast-math-namespace-functions.md#rsqrtf)|傳回對等的引數的平方根|  
|[signbit](concurrency-fast-math-namespace-functions.md#signbit)|傳回引數的符號|  
|[signbitf](concurrency-fast-math-namespace-functions.md#signbitf)|傳回引數的符號|  
|[sin](concurrency-fast-math-namespace-functions.md#sin)|計算引數的正弦值|  
|[sincos](concurrency-fast-math-namespace-functions.md#sincos)|計算正弦函數 」 與 「 餘弦值 _X|  
|[sincosf](concurrency-fast-math-namespace-functions.md#sincosf)|計算正弦函數 」 與 「 餘弦值 _X|  
|[sinf](concurrency-fast-math-namespace-functions.md#sinf)|計算引數的正弦值|  
|[sinh](concurrency-fast-math-namespace-functions.md#sinh)|計算引數的雙曲正弦值|  
|[sinhf](concurrency-fast-math-namespace-functions.md#sinhf)|計算引數的雙曲正弦值|  
|[sqrt](concurrency-fast-math-namespace-functions.md#sqrt)|計算引數的平方根|  
|[sqrtf](concurrency-fast-math-namespace-functions.md#sqrtf)|計算引數的平方根|  
|[tan](concurrency-fast-math-namespace-functions.md#tan)|計算引數的正切函數的值|  
|[tanf](concurrency-fast-math-namespace-functions.md#tanf)|計算引數的正切函數的值|  
|[tanh](concurrency-fast-math-namespace-functions.md#tanh)|計算引數的雙曲正切值|  
|[tanhf](concurrency-fast-math-namespace-functions.md#tanhf)|計算引數的雙曲正切值|  
|[trunc](concurrency-fast-math-namespace-functions.md#trunc)|截斷的整數部分的引數|  
|[truncf](concurrency-fast-math-namespace-functions.md#truncf)|截斷的整數部分的引數|  

## <a name="requirements"></a>需求  
 **標頭：** amp_math.h  
  
 **命名空間：** concurrency:: fast_math  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
