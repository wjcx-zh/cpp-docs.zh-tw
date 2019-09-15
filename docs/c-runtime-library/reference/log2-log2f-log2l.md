---
title: log2、log2f、log2l
ms.date: 04/05/2018
api_name:
- log2
- log2l
- log2f
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
api_type:
- DLLExport
topic_type:
- apiref
ms.assetid: 94d11b38-70b7-4d3a-94ac-523153c92b2e
ms.openlocfilehash: bf1734ea2f96fa1c09b3b0d1f43b681fc31c8f9f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953161"
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

*x*<br/>
要用來判斷以 2 為底數之對數的值。

## <a name="return-value"></a>傳回值

成功時，傳回 log2 *x*。

否則，可能會傳回下列其中一個值：

|問題|Return|
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

如果 x 是整數，則此函式基本上會傳回最具重大1位*x*的以零為基底的索引。

## <a name="requirements"></a>需求

|函數|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**log2**、 **log2f**、 **log2l**|\<math.h>|\<cmath>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[exp2、exp2f、exp2l](exp2-exp2f-exp2l.md)<br/>
[log、logf、log10、log10f](log-logf-log10-log10f.md)<br/>
