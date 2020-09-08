---
title: expm1、expm1f、expm1l
description: Expm1、expm1f 和 expm1 的 API 參考;這會計算值的 e-e 指數，減一。
ms.date: 9/1/2020
api_name:
- expm1l
- expm1
- expm1f
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
f1_keywords:
- expm1l
- expm1
- expm1f
helpviewer_keywords:
- expm1f function
- expm1l function
- expm1 function
ms.assetid: 2a4dd2d9-370c-42b0-9067-0625efa272e0
ms.openlocfilehash: 6d352e91d895cd63c7134faff90bc1bc43a50708
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556498"
---
# <a name="expm1-expm1f-expm1l"></a>expm1、expm1f、expm1l

計算底數為 e 的指數值減一。

## <a name="syntax"></a>語法

```C
double expm1(
   double x
);
float expm1(
   float x
);  // C++ only
long double expm1(
   long double x
);  // C++ only
float expm1f(
   float x
);
long double expm1l(
   long double x
);
#define expm1(X) // Requires C11 or higher
```

### <a name="parameters"></a>參數

*X*\
浮點指數值。

## <a name="return-value"></a>傳回值

如果成功， **expm1** 函數會傳回代表 e<sup>x</sup> -1 的浮點值。 溢位時， **expm1** 會傳回 **HUGE_VAL**、 **expm1f** 會傳回 **HUGE_VALF**、 **expm1l** 會傳回 **HUGE_VALL**，而 **errno** 會設定為 **ERANGE**。 如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用和傳回值的 **expm1** 多載 **`float`** **`long double`** 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **expm1** 一律會採用並傳回 **`double`** 。

如果您使用 \<tgmath.h> `expm1()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**expm1**、 **expm1f**、 **expm1l**|\<math.h>|
|**expm1** 宏 | \<tgmath.h> |

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[exp2、exp2f、exp2l](exp2-exp2f-exp2l.md)<br/>
[pow、powf、powl](pow-powf-powl.md)<br/>
