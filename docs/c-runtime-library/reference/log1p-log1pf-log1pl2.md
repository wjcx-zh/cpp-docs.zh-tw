---
title: log1p、log1pf、log1pl2
description: Log1p、log1pf、log1pl2 的 API 參考;這會計算1的自然對數加上指定的值。
ms.date: 9/1/2020
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
ms.openlocfilehash: 8858d761428d4dad6e3fe836b82041ae92f1827a
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556226"
---
# <a name="log1p-log1pf-log1pl"></a>log1p、log1pf、log1pl

計算 1 加上指定值的自然對數。

## <a name="syntax"></a>語法

```C
double log1p(
   double x
);
float log1pf(
   float x
);
long double log1pl(
   long double x
);

#define log1p(X) // Requires C11 or higher

float log1p(
   float x
); //C++ only

long double log1p(
   long double x
); //C++ only
```

### <a name="parameters"></a>參數

*X*\
浮點引數。

## <a name="return-value"></a>傳回值

如果成功，會傳回 (*x* + 1) 的自然 (base-*e*) 記錄。

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
|± QNaN、不定|與輸入相同|||

如果*x* =-1，則**errno**值會設定為 ERANGE。 如果*x* <-1，則**errno**值會設定為**EDOM** 。

## <a name="remarks"></a>備註

**log1p** `log(x + 1)` 當*x*接近0時，log1p 函式的精確度可能會比使用更為精確。

因為 c + + 允許多載，所以您可以呼叫採用和傳回和類型的 **log1p** 多載 **`float`** **`long double`** 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **log1p** 一律會採用並傳回 **`double`** 。

如果您使用 \<tgmath.h> `log1p()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

如果 *x* 是一個自然數位，此函數會傳回 (*x* -1) 的階乘對數。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**log1p**、 **log1pf**、 **log1pl**|\<math.h>|\<cmath>|
|**log1p** 宏 | \<tgmath.h> ||

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)\
[log2、log2f、log2l](log2-log2f-log2l.md)\
[log、logf、log10、log10f](log-logf-log10-log10f.md)
