---
title: log2、log2f、log2l
description: Log2、log2f 和 log2l 的 API 參考;這會決定二進位 (底數 2) 指定值的對數。
ms.date: 9/1/2020
api_name:
- log2
- log2l
- log2f
- _o_log2
- _o_log2f
- _o_log2l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
ms.assetid: 94d11b38-70b7-4d3a-94ac-523153c92b2e
ms.openlocfilehash: 37319560891dbd64030495750aaf347d9dedd7e7
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555354"
---
# <a name="log2-log2f-log2l"></a>log2、log2f、log2l

判斷指定值的二元 (以 2 為底數) 對數。

## <a name="syntax"></a>語法

```C
double log2(
   double x
);

float log2(
   float x
); //C++ only

long double log2(
   long double x
); //C++ only

float log2f(
   float x
);

long double log2l(
   long double x
);

#define log2(X) // Requires C11 or higher
```

### <a name="parameters"></a>參數

*X*\
要用來判斷以 2 為底數之對數的值。

## <a name="return-value"></a>傳回值

成功時，傳回 log2 *x*。

否則，可能會傳回下列其中一個值：

|問題|傳回|
|-----------|------------|
|*x* < 0|NaN|
|*x* = ±0|-INFINITY|
|*x* = 1|+0|
|+INFINITY|+INFINITY|
|NaN|NaN|
|網域錯誤|NaN|
|極錯誤|-HUGE_VAL、-HUGE_VALF 或 -HUGE_VALL|

依 [_matherr](matherr.md) 中的指定回報錯誤。

## <a name="remarks"></a>備註

如果 *x* 是整數，此函式基本上會傳回最顯著1位 *x*的以零為基底的索引。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**log2**、 **log2f**、 **log2l**|\<math.h>|\<cmath>|
|**log2** 宏 | \<tgmath.h> ||

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)<br/>
[exp2、exp2f、exp2l](exp2-exp2f-exp2l.md)<br/>
[log、logf、log10、log10f](log-logf-log10-log10f.md)<br/>
