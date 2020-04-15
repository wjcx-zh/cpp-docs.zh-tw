---
title: lgamma、lgammaf、lgammal
ms.date: 4/2/2020
api_name:
- lgamma
- lgammaf
- lgammal
- _o_lgamma
- _o_lgammaf
- _o_lgammal
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lgamma
- lgammaf
- lgammal
- math/lgamma
- math/lgammaf
- math/lgammal
helpviewer_keywords:
- lgamma function
- lgammal function
- lgammaf function
ms.assetid: 6e326c58-7077-481a-a329-c82ae56ae9e6
ms.openlocfilehash: e2bdfbeac7b995be0b589156437a3ded39114adf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342154"
---
# <a name="lgamma-lgammaf-lgammal"></a>lgamma、lgammaf、lgammal

判斷指定值之 gamma 函式絕對值的自然對數。

## <a name="syntax"></a>語法

```C
double lgamma( double x );
float lgammaf( float x );
long double lgammal( long double x );
```

```cpp
float lgamma( float x ); //C++ only
long double lgamma( long double x ); //C++ only
```

### <a name="parameters"></a>參數

*X.*<br/>
要計算的值。

## <a name="return-value"></a>傳回值

如果成功,返回*x*的 gamma 函數的絕對值的自然對數。

|問題|傳回|
|-----------|------------|
|*x* = NaN|NaN|
|*x* = |0|+INFINITY|
|*x*= 負整數|+INFINITY|
|*無限|+INFINITY|
|極錯誤|+HUGE_VAL、+HUGE_VALF 或 +HUGE_VALL|
|溢位範圍錯誤|[HUGE_VAL、HUGE_VALF 或 HUGE_VALL|

依 [_matherr](matherr.md) 中的指定回報錯誤。

## <a name="remarks"></a>備註

由於C++允許重載,因此可以調用**lgamma**的重載,這些重載和返回**浮點**和**長****雙**類型。 在 C 程式中 **,lgamma**始終取得並返回**一個雙**。

如果 x 是一個合理數位,則此函數返回因數m的對數 (x - 1)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**lgamma,** **lgammaf,** **lgaml**|\<math.h>|\<cmath>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[tgamma、tgammaf、tgammal](tgamma-tgammaf-tgammal.md)<br/>
