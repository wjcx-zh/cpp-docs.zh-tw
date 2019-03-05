---
title: Concurrency::fast_math 命名空間
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::fast_math
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
ms.openlocfilehash: e774c2d8e4431960e796ee1e6cc87b924d04174b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287956"
---
# <a name="concurrencyfastmath-namespace"></a>Concurrency::fast_math 命名空間

中的函式`fast_math`命名空間具有較低的精確度，支援唯一的單精確度 (`float`)，並呼叫 DirectX 內建函式。 有兩個版本的每個函式，例如`cos`和`cosf`。 這兩個版本，並傳回`float`，但各自呼叫相同的 DirectX 內建函式。

## <a name="syntax"></a>語法

```
namespace fast_math;
```

## <a name="members"></a>成員

### <a name="functions"></a>函式

|名稱|描述|
|----------|-----------------|
|[cos](concurrency-fast-math-namespace-functions.md#cos)|計算引數的反餘弦值|
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|計算引數的反餘弦值|
|[asin](concurrency-fast-math-namespace-functions.md#asin)|計算引數的反正弦值|
|[asinf](concurrency-fast-math-namespace-functions.md#asinf)|計算引數的反正弦值|
|[atan](concurrency-fast-math-namespace-functions.md#atan)|計算引數的反正切值|
|[atan2](concurrency-fast-math-namespace-functions.md#atan2)|計算 _Y/_X 的反正切值|
|[atan2f](concurrency-fast-math-namespace-functions.md#atan2f)|計算 _Y/_X 的反正切值|
|[atanf](concurrency-fast-math-namespace-functions.md#atanf)|計算引數的反正切值|
|[ceil](concurrency-fast-math-namespace-functions.md#ceil)|計算引數的上限|
|[ceilf](concurrency-fast-math-namespace-functions.md#ceilf)|計算引數的上限|
|[cos](concurrency-fast-math-namespace-functions.md#cos)|計算引數的餘弦函數|
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|計算引數的餘弦函數|
|[cosh](concurrency-fast-math-namespace-functions.md#cosh)|計算引數的雙曲餘弦值|
|[coshf](concurrency-fast-math-namespace-functions.md#coshf)|計算引數的雙曲餘弦值|
|[exp](concurrency-fast-math-namespace-functions.md#exp)|計算底數為 e 引數的指數|
|[exp2](concurrency-fast-math-namespace-functions.md#exp2)|計算基底 2 指數的引數|
|[exp2f](concurrency-fast-math-namespace-functions.md#exp2f)|計算基底 2 指數的引數|
|[expf](concurrency-fast-math-namespace-functions.md#expf)|計算底數為 e 引數的指數|
|[fabs](concurrency-fast-math-namespace-functions.md#fabs)|傳回引數的絕對值|
|[fabsf](concurrency-fast-math-namespace-functions.md#fabsf)|傳回引數的絕對值|
|[floor](concurrency-fast-math-namespace-functions.md#floor)|計算引數的最小|
|[floorf](concurrency-fast-math-namespace-functions.md#floorf)|計算引數的最小|
|[fmax](concurrency-fast-math-namespace-functions.md#fmax)|判斷引數的最大數值|
|[fmaxf](concurrency-fast-math-namespace-functions.md#fmaxf)|判斷引數的最大數值|
|[fmin](concurrency-fast-math-namespace-functions.md#fmin)|判斷引數的最小數值|
|[fminf](concurrency-fast-math-namespace-functions.md#fminf)|判斷引數的最小數值|
|[fmod](concurrency-fast-math-namespace-functions.md#fmod)|計算 _X/_Y 浮點數餘數|
|[fmodf](concurrency-fast-math-namespace-functions.md#fmodf)|計算 _X/_Y 浮點數餘數|
|[frexp](concurrency-fast-math-namespace-functions.md#frexp)|取得的尾數和指數 _X|
|[frexpf](concurrency-fast-math-namespace-functions.md#frexpf)|取得的尾數和指數 _X|
|[isfinite](concurrency-fast-math-namespace-functions.md#isfinite)|判斷引數值是否有限的值|
|[isinf](concurrency-fast-math-namespace-functions.md#isinf)|判斷引數是否為無限大的值|
|[isnan](concurrency-fast-math-namespace-functions.md#isnan)|判斷引數是否為 NaN|
|[ldexp](concurrency-fast-math-namespace-functions.md#ldexp)|計算出實數從的尾數和指數|
|[ldexpf](concurrency-fast-math-namespace-functions.md#ldexpf)|計算出實數從的尾數和指數|
|[log](concurrency-fast-math-namespace-functions.md#log)|計算引數的基底 e 對數|
|[log10](concurrency-fast-math-namespace-functions.md#log10)|計算引數的基底 10 對數|
|[log10f](concurrency-fast-math-namespace-functions.md#log10f)|計算引數的基底 10 對數|
|[log2](concurrency-fast-math-namespace-functions.md#log2)|計算引數的基底 2 對數|
|[log2f](concurrency-fast-math-namespace-functions.md#log2f)|計算引數的基底 2 對數|
|[logf](concurrency-fast-math-namespace-functions.md#logf)|計算引數的基底 e 對數|
|[modf](concurrency-fast-math-namespace-functions.md#modf)|將 _X 成小數和整數部分。|
|[modff](concurrency-fast-math-namespace-functions.md#modff)|將 _X 成小數和整數部分。|
|[pow](concurrency-fast-math-namespace-functions.md#pow)|計算 _X 的 _y 次方|
|[powf](concurrency-fast-math-namespace-functions.md#powf)|計算 _X 的 _y 次方|
|[round](concurrency-fast-math-namespace-functions.md#round)|會四捨五入為最接近整數的 _X|
|[roundf](concurrency-fast-math-namespace-functions.md#roundf)|會四捨五入為最接近整數的 _X|
|[rsqrt](concurrency-fast-math-namespace-functions.md#rsqrt)|傳回引數的平方根的倒數|
|[rsqrtf](concurrency-fast-math-namespace-functions.md#rsqrtf)|傳回引數的平方根的倒數|
|[signbit](concurrency-fast-math-namespace-functions.md#signbit)|傳回引數的正負號|
|[signbitf](concurrency-fast-math-namespace-functions.md#signbitf)|傳回引數的正負號|
|[sin](concurrency-fast-math-namespace-functions.md#sin)|計算引數的正弦值|
|[sincos](concurrency-fast-math-namespace-functions.md#sincos)|計算 _X 的正弦和餘弦值|
|[sincosf](concurrency-fast-math-namespace-functions.md#sincosf)|計算 _X 的正弦和餘弦值|
|[sinf](concurrency-fast-math-namespace-functions.md#sinf)|計算引數的正弦值|
|[sinh](concurrency-fast-math-namespace-functions.md#sinh)|計算引數的雙曲正弦值|
|[sinhf](concurrency-fast-math-namespace-functions.md#sinhf)|計算引數的雙曲正弦值|
|[sqrt](concurrency-fast-math-namespace-functions.md#sqrt)|計算引數的平方根|
|[sqrtf](concurrency-fast-math-namespace-functions.md#sqrtf)|計算引數的平方根|
|[tan](concurrency-fast-math-namespace-functions.md#tan)|計算引數的正切值|
|[tanf](concurrency-fast-math-namespace-functions.md#tanf)|計算引數的正切值|
|[tanh](concurrency-fast-math-namespace-functions.md#tanh)|計算引數的雙曲正切值|
|[tanhf](concurrency-fast-math-namespace-functions.md#tanhf)|計算引數的雙曲正切值|
|[trunc](concurrency-fast-math-namespace-functions.md#trunc)|引數截斷成整數部分|
|[truncf](concurrency-fast-math-namespace-functions.md#truncf)|引數截斷成整數部分|

## <a name="requirements"></a>需求

**標頭：** amp_math.h

**命名空間：** Concurrency::fast_math

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
