---
title: fabs、fabsf、fabsl
description: Fabs、fabsf 和 fabsl 的 API 參考;，計算浮點值的絕對值。
ms.date: 08/31/2020
api_name:
- fabsf
- fabs
- fabsl
- _o_fabs
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
- fabs
- fabsf
- fabsl
- "math\fabs"
- "math\fabsf"
- "math\fabsl"
helpviewer_keywords:
- absolute values
- fabsf function
- calculating absolute values
- fabs function
- fabsl function
ms.assetid: 23bca210-f408-4f5e-b46b-0ccaaec31e36
ms.openlocfilehash: a819172fc94224ff4c51c8fc342b142ffbe05ae7
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89554834"
---
# <a name="fabs-fabsf-fabsl"></a>fabs、fabsf、fabsl

計算浮點引數的絕對值。

## <a name="syntax"></a>語法

```C
double fabs(
   double x
);
float fabs(
   float x
); // C++ only
long double fabs(
   long double x
); // C++ only
float fabsf(
   float x
);
long double fabsl(
   long double x
);

#define fabs(X) // Requires C11 or higher
```

### <a name="parameters"></a>參數

*X*\
浮點值。

## <a name="return-value"></a>傳回值

**Fabs**函數會傳回引數*x*的絕對值。 不會傳回錯誤。

|輸入|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|± QNAN、IND|無|_DOMAIN|

## <a name="remarks"></a>備註

C + + 允許多載，因此您可以在包含標頭的情況下呼叫 **fabs** 的多載 \<cmath> 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **fabs** 一律會採用並傳回 **`double`** 。

如果您使用 \<tgmath.h> `fabs()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|函式|必要的 C 標頭|必要的 C++ 標頭|
|--------------|-----------------------|---------------------------|
|**fabs**、 **fabsf**、 **fabsl**|\<math.h>|\<cmath> 或 \<math.h>|
|**fabs** 宏 | \<tgmath.h> ||

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [abs](abs-labs-llabs-abs64.md) 的範例。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[abs、labs、llabs、_abs64](abs-labs-llabs-abs64.md)<br/>
[_cabs](cabs.md)<br/>
