---
title: log2、log2f、log2l
ms.date: 4/2/2020
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
ms.assetid: 94d11b38-70b7-4d3a-94ac-523153c92b2e
ms.openlocfilehash: 29a1a9e2003091944a4587036c62a49d76333080
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341713"
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
```

### <a name="parameters"></a>參數

*X.*<br/>
要用來判斷以 2 為底數之對數的值。

## <a name="return-value"></a>傳回值

成功後,傳回回日誌 2 *x*。

否則，可能會傳回下列其中一個值：

|問題|傳回|
|-----------|------------|
|*x* < 0|NaN|
|*x* = |0|-INFINITY|
|*x* = 1|+0|
|+INFINITY|+INFINITY|
|NaN|NaN|
|網域錯誤|NaN|
|極錯誤|-HUGE_VAL、-HUGE_VALF 或 -HUGE_VALL|

依 [_matherr](matherr.md) 中的指定回報錯誤。

## <a name="remarks"></a>備註

如果 x 是整數,則此函數實質上返回最重要的 1 位*x*的零基索引。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**紀錄2**,**紀錄2f**, **log2l**|\<math.h>|\<cmath>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[exp2、exp2f、exp2l](exp2-exp2f-exp2l.md)<br/>
[log、logf、log10、log10f](log-logf-log10-log10f.md)<br/>
