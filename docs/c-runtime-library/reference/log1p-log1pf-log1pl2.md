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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: b4e077f5b806dbe38ed4a4f4e8eef0259170cb7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341815"
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

*X.*<br/>
浮點引數。

## <a name="return-value"></a>傳回值

如果成功,則返回 (*x* = 1) 的自然 (基 *-e*) 日誌。

否則，可能會傳回下列其中一個值：

|輸入|結果|SEH 例外狀況|errno|
|-----------|------------|-------------------|-----------|
|+inf|+inf|||
|非正規數|與輸入相同|UNDERFLOW||
|±0|與輸入相同|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1|nan|無效|EDOM|
|-inf|nan|無效|EDOM|
|*SNaN|與輸入相同|無效||
|*QNaN,無限期|與輸入相同|||

如果*x* = -1,**則 errno**值設定為 ERANGE。 如果*x* < -1,**則 errno**值設置為**EDOM。**

## <a name="remarks"></a>備註

**log1p**函數可能比 當`log(x + 1)`*x*接近 0 時使用更準確。

由於C++允許重載,因此可以調用**log1p**的重載,這些重載和返回**浮點**和**長****雙**類型。 在 C 程式中 **,log1p**始終採用並傳回**一個雙**。

如果*x*是自然數位,則此函數返回 (*x* - 1) 因數的對數。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**紀錄1p**,**紀錄1pf**,**紀錄1pl**|\<math.h>|\<cmath>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[log2、log2f、log2l](log2-log2f-log2l.md)<br/>
[log、logf、log10、log10f](log-logf-log10-log10f.md)<br/>
