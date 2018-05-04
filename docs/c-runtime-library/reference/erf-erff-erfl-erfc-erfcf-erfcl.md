---
title: erf、erff、erfl、erfc、erfcf、erfcl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- erff
- erfl
- erf
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
- erfl
- erf
- erff
dev_langs:
- C++
helpviewer_keywords:
- erfl function
- erff function
- erf function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b7ab1448c3f1d77ab79266858a19d822b1cdb4f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
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

*x*<br/>
浮點值。

## <a name="return-value"></a>傳回值

**Erf**函式會傳回高斯錯誤函式*x*。 **Erfc**函式會傳回的補充高斯錯誤函式*x*。

## <a name="remarks"></a>備註

**Erf**函數會計算的高斯錯誤函式*x*，其定義為：

![x 的誤差函式](media/crt_erf_formula.PNG "CRT_erf_formula")

補充高斯錯誤函式定義為 1-erf （x)。 **Erf**函式傳回的值範圍為-1.0 到 1.0。 不會傳回錯誤。 **Erfc**函式會傳回範圍 0 到 2 中的值。 如果*x*而言太大**erfc**、 **errno**變數會設為**為 ERANGE**。

因為 c + + 允許多載，所以您可以呼叫的多載**erf**和**erfc**採用並傳回**float**和**長** **double**型別。 在 C 程式中， **erf**和**erfc**一律採用並傳回**double**。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**erf**， **erff**， **erfl**， **erfc**， **erfcf**， **erfcl**|\<math.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
