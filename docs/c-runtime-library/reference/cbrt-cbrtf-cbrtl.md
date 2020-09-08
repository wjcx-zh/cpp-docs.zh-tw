---
title: cbrt、cbrtf、cbrtl
description: Cbrt、cbrtf 和 cbrtl 的 API 參考;計算 cube 根目錄的
ms.date: 9/1/2020
api_name:
- cbrt
- cbrtf
- cbrtl
- _o_cbrt
- _o_cbrtf
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
- cbrtl
- cbrt
- cbrtf
helpviewer_keywords:
- cbrtl function
- cbrtf function
- cbrt function
ms.assetid: ab51d916-3db2-4beb-b46a-28b4062cd33f
ms.openlocfilehash: c63a3cb0c8acdec8ef66999994ab1f3c5ea21d47
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555302"
---
# <a name="cbrt-cbrtf-cbrtl"></a>cbrt、cbrtf、cbrtl

計算立方根。

## <a name="syntax"></a>語法

```C
double cbrt(
   double x
);
float cbrt(
   float x
);  // C++ only
long double cbrt(
   long double x
);  // C++ only
float cbrtf(
   float x
);
long double cbrtl(
   long double x
);
#define cbrt(X) // Requires C11 or higher
```

### <a name="parameters"></a>參數

*X*\
浮點值。

## <a name="return-value"></a>傳回值

**Cbrt**函數會傳回*x*的立方根。

|輸入|SEH 例外狀況|**_matherr** 例外|
|-----------|-------------------|--------------------------|
|±∞、QNAN、IND|無|無|

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用或類型之 **cbrt** 的多載 **`float`** **`long double`** 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **cbrt** 一律會採用並傳回 **`double`** 。

如果您使用 \<tgmath.h> `cbrt()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**cbrt**、 **cbrtf**、 **cbrtl**|\<math.h>|\<cmath>|
|**cbrt** 宏 | \<tgmath.h> ||

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_cbrt.c
// Compile using: cl /W4 crt_cbrt.c
// This program calculates a cube root.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double question = -64.64;
   double answer;

   answer = cbrt(question);
   printf("The cube root of %.2f is %.6f\n", question, answer);
}
```

```Output
The cube root of -64.64 is -4.013289
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[exp、expf、expl](exp-expf.md)<br/>
[log、logf、log10、log10f](log-logf-log10-log10f.md)<br/>
[pow、powf、powl](pow-powf-powl.md)<br/>
