---
title: Concurrency::fast_math 命名空間
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::fast_math
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
ms.openlocfilehash: 57e2134a2254dc4bc34d515e65e2ec629efeff33
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139516"
---
# <a name="concurrencyfast_math-namespace"></a>Concurrency::fast_math 命名空間

`fast_math` 命名空間中的函式具有較低的精確度、僅支援單精確度（`float`），並呼叫 DirectX 內建函式。 每個函數都有兩個版本，例如 `cos` 和 `cosf`。 這兩個版本都採用並傳回 `float`，但每個都會呼叫相同的 DirectX 內建函式。

## <a name="syntax"></a>語法

```cpp
namespace fast_math;
```

## <a name="members"></a>成員

### <a name="functions"></a>函式

|名稱|描述|
|----------|-----------------|
|[cos](concurrency-fast-math-namespace-functions.md#cos)|計算引數的反余弦|
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|計算引數的反余弦|
|[asin](concurrency-fast-math-namespace-functions.md#asin)|計算引數的反正弦|
|[asinf](concurrency-fast-math-namespace-functions.md#asinf)|計算引數的反正弦|
|[atan](concurrency-fast-math-namespace-functions.md#atan)|計算引數的反正切|
|[atan2](concurrency-fast-math-namespace-functions.md#atan2)|計算 _Y/_X 的反正切值|
|[atan2f](concurrency-fast-math-namespace-functions.md#atan2f)|計算 _Y/_X 的反正切值|
|[atanf](concurrency-fast-math-namespace-functions.md#atanf)|計算引數的反正切|
|[ceil](concurrency-fast-math-namespace-functions.md#ceil)|計算引數的上限|
|[ceilf](concurrency-fast-math-namespace-functions.md#ceilf)|計算引數的上限|
|[cos](concurrency-fast-math-namespace-functions.md#cos)|計算引數的餘弦|
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|計算引數的餘弦|
|[cosh](concurrency-fast-math-namespace-functions.md#cosh)|計算引數的雙曲余弦值|
|[coshf](concurrency-fast-math-namespace-functions.md#coshf)|計算引數的雙曲余弦值|
|[exp](concurrency-fast-math-namespace-functions.md#exp)|計算引數的以 e 為底數的指數|
|[exp2](concurrency-fast-math-namespace-functions.md#exp2)|計算引數的基底2指數|
|[exp2f](concurrency-fast-math-namespace-functions.md#exp2f)|計算引數的基底2指數|
|[expf](concurrency-fast-math-namespace-functions.md#expf)|計算引數的以 e 為底數的指數|
|[fabs](concurrency-fast-math-namespace-functions.md#fabs)|傳回引數的絕對值。|
|[fabsf](concurrency-fast-math-namespace-functions.md#fabsf)|傳回引數的絕對值。|
|[floor](concurrency-fast-math-namespace-functions.md#floor)|計算引數的樓層|
|[floorf](concurrency-fast-math-namespace-functions.md#floorf)|計算引數的樓層|
|[fmax](concurrency-fast-math-namespace-functions.md#fmax)|判斷引數的最大數值|
|[fmaxf](concurrency-fast-math-namespace-functions.md#fmaxf)|判斷引數的最大數值|
|[fmin](concurrency-fast-math-namespace-functions.md#fmin)|判斷引數的最小數值|
|[fminf](concurrency-fast-math-namespace-functions.md#fminf)|判斷引數的最小數值|
|[fmod](concurrency-fast-math-namespace-functions.md#fmod)|計算 _X/_Y 的浮點餘數|
|[fmodf](concurrency-fast-math-namespace-functions.md#fmodf)|計算 _X/_Y 的浮點餘數|
|[frexp](concurrency-fast-math-namespace-functions.md#frexp)|取得 _X 的尾數和指數|
|[frexpf](concurrency-fast-math-namespace-functions.md#frexpf)|取得 _X 的尾數和指數|
|[isfinite](concurrency-fast-math-namespace-functions.md#isfinite)|判斷引數是否有有限值|
|[isinf](concurrency-fast-math-namespace-functions.md#isinf)|判斷引數是否為無限大|
|[isnan](concurrency-fast-math-namespace-functions.md#isnan)|判斷引數是否為 NaN|
|[ldexp](concurrency-fast-math-namespace-functions.md#ldexp)|計算尾數和指數中的實數|
|[ldexpf](concurrency-fast-math-namespace-functions.md#ldexpf)|計算尾數和指數中的實數|
|[log](concurrency-fast-math-namespace-functions.md#log)|計算引數的以 e 為底數的對數|
|[log10](concurrency-fast-math-namespace-functions.md#log10)|計算引數的以10為底數的對數|
|[log10f](concurrency-fast-math-namespace-functions.md#log10f)|計算引數的以10為底數的對數|
|[log2](concurrency-fast-math-namespace-functions.md#log2)|計算引數的以2為底數的對數|
|[log2f](concurrency-fast-math-namespace-functions.md#log2f)|計算引數的以2為底數的對數|
|[logf](concurrency-fast-math-namespace-functions.md#logf)|計算引數的以 e 為底數的對數|
|[modf](concurrency-fast-math-namespace-functions.md#modf)|將 _X 分割成小數和整數部分。|
|[modff](concurrency-fast-math-namespace-functions.md#modff)|將 _X 分割成小數和整數部分。|
|[pow](concurrency-fast-math-namespace-functions.md#pow)|計算 _X _Y 的乘冪|
|[powf](concurrency-fast-math-namespace-functions.md#powf)|計算 _X _Y 的乘冪|
|[round](concurrency-fast-math-namespace-functions.md#round)|將 _X 四捨五入到最接近的整數|
|[roundf](concurrency-fast-math-namespace-functions.md#roundf)|將 _X 四捨五入到最接近的整數|
|[rsqrt](concurrency-fast-math-namespace-functions.md#rsqrt)|傳回引數平方根的倒數|
|[rsqrtf](concurrency-fast-math-namespace-functions.md#rsqrtf)|傳回引數平方根的倒數|
|[signbit](concurrency-fast-math-namespace-functions.md#signbit)|傳回引數的正負號|
|[signbitf](concurrency-fast-math-namespace-functions.md#signbitf)|傳回引數的正負號|
|[sin](concurrency-fast-math-namespace-functions.md#sin)|計算引數的正弦值|
|[sincos](concurrency-fast-math-namespace-functions.md#sincos)|計算 _X 的正弦和余弦值|
|[sincosf](concurrency-fast-math-namespace-functions.md#sincosf)|計算 _X 的正弦和余弦值|
|[sinf](concurrency-fast-math-namespace-functions.md#sinf)|計算引數的正弦值|
|[sinh](concurrency-fast-math-namespace-functions.md#sinh)|計算引數的雙曲正弦值|
|[sinhf](concurrency-fast-math-namespace-functions.md#sinhf)|計算引數的雙曲正弦值|
|[sqrt](concurrency-fast-math-namespace-functions.md#sqrt)|計算引數的平方根|
|[sqrtf](concurrency-fast-math-namespace-functions.md#sqrtf)|計算引數的平方根|
|[tan](concurrency-fast-math-namespace-functions.md#tan)|計算引數的正切值|
|[tanf](concurrency-fast-math-namespace-functions.md#tanf)|計算引數的正切值|
|[tanh](concurrency-fast-math-namespace-functions.md#tanh)|計算引數的雙曲正切值|
|[tanhf](concurrency-fast-math-namespace-functions.md#tanhf)|計算引數的雙曲正切值|
|[trunc](concurrency-fast-math-namespace-functions.md#trunc)|截斷整陣列件的引數|
|[truncf](concurrency-fast-math-namespace-functions.md#truncf)|截斷整陣列件的引數|

## <a name="requirements"></a>需求

**標頭：** amp_math。h

**命名空間：** Concurrency：： fast_math

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
