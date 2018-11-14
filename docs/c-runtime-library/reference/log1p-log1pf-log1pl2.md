---
title: log1p log1pf log1pl2
ms.date: 04/05/2018
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
ms.openlocfilehash: 2ac864d7e28823c95b0202c0a8f2454d03c64aff
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519302"
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

如果成功，傳回的自然 (底數為*電子*) 的記錄 (*x* + 1)。

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
|±QNaN，無限制|與輸入相同|||

**Errno**如果值設為 ERANGE *x* =-1。 **Errno**值設定為**EDOM**如果*x* <-1。

## <a name="remarks"></a>備註

**Log1p**函式可能比使用更準確`log(x + 1)`當*x*趨近於 0。

因為 c + + 允許多載，您可以呼叫多載**log1p**採用並傳回**float**並**長** **double**類型。 在 C 程式中， **log1p**一律採用並傳回**double**。

如果*x*為自然數，此函數會傳回階乘的對數 (*x* -1)。

## <a name="requirements"></a>需求

|功能|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**log1p**， **log1pf**， **log1pl**|\<math.h>|\<cmath>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[log2、log2f、log2l](log2-log2f-log2l.md)<br/>
[log、logf、log10、log10f](log-logf-log10-log10f.md)<br/>
