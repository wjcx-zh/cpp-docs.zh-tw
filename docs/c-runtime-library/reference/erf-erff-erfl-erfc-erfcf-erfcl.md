---
title: erf、erff、erfl、erfc、erfcf、erfcl
ms.date: 4/2/2020
api_name:
- erff
- erfl
- erf
- erfc
- erfcf
- erfcl
- _o_erf
- _o_erfc
- _o_erfcf
- _o_erfcl
- _o_erff
- _o_erfl
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
- erfl
- erf
- erff
- erfc
- erfcf
- erfcl
helpviewer_keywords:
- erfl function
- erff function
- erf function
- erfcl function
- erfcf function
- erfc function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
ms.openlocfilehash: ad7ad279d3686e4f33a6f5f901c60348c131b89a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347915"
---
# <a name="erf-erff-erfl-erfc-erfcf-erfcl"></a>erf、erff、erfl、erfc、erfcf、erfcl

計算值的錯誤函式或補充錯誤函式。

## <a name="syntax"></a>語法

```C
double erf(
   double x
);
float erf(
   float x
); // C++ only
long double erf(
   long double x
); // C++ only
float erff(
   float x
);
long double erfl(
   long double x
);
double erfc(
   double x
);
float erfc(
   float x
); // C++ only
long double erfc(
   long double x
); // C++ only
float erfcf(
   float x
);
long double erfcl(
   long double x
);
```

### <a name="parameters"></a>參數

*X.*<br/>
浮點值。

## <a name="return-value"></a>傳回值

**erf**函數傳回*x*的高斯錯誤函數 。 **erfc**函數傳回*x*的互補高斯誤差函數。

## <a name="remarks"></a>備註

**erf**函數計算*x*的高斯誤差函數,該函數定義為:

![x 的誤差函式值](media/crt_erf_formula.PNG "x 的誤差函式值")

互補高斯誤差函數定義為 1 - erf(x)。 **erf**函數傳回範圍 -1.0 到 1.0 中的值。 不會傳回錯誤。 **erfc**函數返回範圍 0 到 2 中的值。 如果*x*對於**erfc**來說太大,則**errno**變數設定為**ERANGE**。

由於C++允許重載,因此可以調用獲取和返回**浮點**和**長****雙**類型的**erf**和**erfc**的重載。 在C程式中 **,erf**和**erfc**總是將傳**回一個雙**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**埃爾夫**,**埃爾夫**,**埃爾弗爾**,**埃爾夫夫**,**埃爾夫夫**,**埃爾夫**|\<math.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
