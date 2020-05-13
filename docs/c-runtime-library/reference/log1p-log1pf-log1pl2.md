---
title: log1p、log1pf、log1pl2
ms.date: 4/2/2020
api_name:
- log1p
- log1pf
- log1pl
- _o_log1p
- _o_log1pf
- _o_log1pl
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
f1_keywords:
- log1p
- log1pf
- log1pl
- math/log1p
- math/log1pf
- math/log1pl
helpviewer_keywords:
- log1p function
- log1pf function
- log1pl function
ms.assetid: a40d965d-b4f6-42f4-ba27-2395546f7c12
ms.openlocfilehash: 21bba72b204f975b806e43cdc6d36d8efa173b9b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911433"
---
# <a name="log1p-log1pf-log1pl"></a>log1p、log1pf、log1pl

計算 1 加上指定值的自然對數。

## <a name="syntax"></a>語法

```C
double log1p(
   double x
);

float log1p(
   float x
); //C++ only

long double log1p(
   long double x
); //C++ only

float log1pf(
   float x
);

long double log1pl(
   long double x
);
```

### <a name="parameters"></a>參數

*x*<br/>
浮點引數。

## <a name="return-value"></a>傳回值

如果成功，會傳回（*x* + 1）的自然（base-*e*）記錄。

否則，可能會傳回下列其中一個值：

|輸入|結果|SEH 例外狀況|errno|
|-----------|------------|-------------------|-----------|
|+inf|+inf|||
|非正規數|與輸入相同|UNDERFLOW||
|±0|與輸入相同|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1|nan|無效|EDOM|
|-inf|nan|無效|EDOM|
|± SNaN|與輸入相同|無效||
|± QNaN，不定|與輸入相同|||

如果*x* =-1， **errno**值會設定為 ERANGE。 如果*x* <-1， **errno**值會設定為**EDOM** 。

## <a name="remarks"></a>備註

當*x*接近0時， **log1p**函數可能`log(x + 1)`會比使用更精確。

因為 c + + 允許多載，所以您可以呼叫採用並傳回**float**和**long** **double**類型之**log1p**的多載。 在 C 程式中， **log1p**一律會採用並傳回**雙精度浮點數**。

如果*x*是自然數位，此函數會傳回（*x* -1）階乘的對數。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**log1p**、 **log1pf**、 **log1pl**|\<math.h>|\<cmath>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[log2、log2f、log2l](log2-log2f-log2l.md)<br/>
[log、logf、log10、log10f](log-logf-log10-log10f.md)<br/>
