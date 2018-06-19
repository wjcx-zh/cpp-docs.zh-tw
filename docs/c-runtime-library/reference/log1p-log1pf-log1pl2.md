---
title: log1p、log1pf、log1pl2 | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- log1p
- log1pf
- log1pl
apilocation:
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
apitype: DLLExport
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 650fb8f7567b4f2f3b0b9032397c2b54a99013dd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402744"
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

如果成功，傳回的自然 (基底-*e*) 的記錄 (*x* + 1)。

否則，可能會傳回下列其中一個值：

|輸入|結果|SEH 例外狀況|errno|
|-----------|------------|-------------------|-----------|
|+inf|+inf|||
|非正規數|與輸入相同|UNDERFLOW||
|±0|與輸入相同|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1|NAN|INVALID|EDOM|
|-inf|NAN|INVALID|EDOM|
|±SNaN|與輸入相同|INVALID||
|無限期 ±QNaN|與輸入相同|||

**Errno**值將設為 ERANGE 如果*x* =-1。 **Errno**值設定為**EDOM**如果*x* <-1。

## <a name="remarks"></a>備註

**Log1p**函式可能會比使用更精確`log(x + 1)`時*x*接近 0。

因為 c + + 允許多載，所以您可以呼叫的多載**log1p**採用並傳回**float**和**長** **double**型別。 在 C 程式中， **log1p**一律採用並傳回**double**。

如果*x*是自然數字，此函式傳回的階乘的對數 (*x* -1)。

## <a name="requirements"></a>需求

|功能|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**log1p**， **log1pf**， **log1pl**|\<math.h>|\<cmath>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[log2、log2f、log2l](log2-log2f-log2l.md)<br/>
[log、logf、log10、log10f](log-logf-log10-log10f.md)<br/>
