---
title: cosh、coshf、coshl
description: Cosh、coshf 和 coshl 的 API 參考;計算浮點值之雙曲余弦值的。
ms.date: 08/31/2020
api_name:
- cosh
- coshf
- coshl
- _o_cosh
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
- cosh
- coshf
- coshl
helpviewer_keywords:
- cosh function
- coshf function
- coshl function
- trigonometric functions
- hyperbolic functions
ms.openlocfilehash: 0ea4a5b77850e196c29519ac49b589a0c2b6c9a7
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555523"
---
# <a name="cosh-coshf-coshl"></a>cosh、coshf、coshl

計算雙曲余弦。

## <a name="syntax"></a>語法

```C
double cosh( double x );
float coshf( float x );
long double coshl( long double x );
#define cosh(X) // Requires C11 or higher

float cosh( float x );  // C++ only
long double cosh( long double x );  // C++ only
```

### <a name="parameters"></a>參數

*X*\
角度 (弧度)。

## <a name="return-value"></a>傳回值

*X*的雙曲余弦值。

根據預設，如果在 **cosh**、 **coshf**或 **coshl** 呼叫中的結果太大，函數會傳回 **HUGE_VAL** ，並將 **errno** 設定為 **ERANGE**。

|輸入|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|± **QNAN**、 **IND**|無|**_DOMAIN**|
|*x* ≥ 7.104760 e + 002|不**精確** +**溢**位|**溢出**|

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用和傳回或值的 **cosh** 多載 **`float`** **`long double`** 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **cosh** 一律會採用並傳回 **`double`** 。

如果您使用 \<tgmath.h> `cosh()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭 (C)|必要的標頭 (C++)|
|-------------|---------------------|-|
|**coshf**、 **cosl**、 **coshl**|\<math.h>|\<cmath> 或 \<math.h>|
|**coshf ( # B1 ** 宏 | \<tgmath.h> ||

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [sinh、sinhf、sinhl](sinh-sinhf-sinhl.md)中的範例。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[acosh、acoshf、acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh、asinhf、asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh、atanhf、atanhl](atanh-atanhf-atanhl.md)<br/>
[_matherr](matherr.md)<br/>
[sinh、sinhf、sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh、tanhf、tanhl](tanh-tanhf-tanhl.md)<br/>
