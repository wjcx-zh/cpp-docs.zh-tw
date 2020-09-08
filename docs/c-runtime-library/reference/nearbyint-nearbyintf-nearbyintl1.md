---
title: nearbyint、nearbyintf、nearbyintl
description: Nearbyint、nearbyintf 和 nearbyintl 的 API 參考;這會將指定的浮點值四捨五入為整數，並以浮點數格式傳回該值。
ms.date: 9/1/2020
api_name:
- nearbyint
- nearbyintf
- nearbyintl
- _o_nearbyint
- _o_nearbyintf
- _o_nearbyintl
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
- nearbyint
- nearbyintf
- nearbyintl
- math/nearbyint
- math/narbyintf
- math/narbyintl
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
ms.openlocfilehash: 9717559518032c6f1f2126c7ded7cb90603bce64
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556381"
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint、nearbyintf、nearbyintl

將指定的浮點值四捨五入成整數，並以浮點數格式傳回該值。

## <a name="syntax"></a>語法

```C
double nearbyint( double x );
float nearbyintf( float x );
long double nearbyintl( long double x );
#define nearbyint( X ) // Requires C11 or higher

float nearbyint( float x ); //C++ only
long double nearbyint( long double x ); //C++ only
```

### <a name="parameters"></a>參數

*X*\
要捨入的值。

## <a name="return-value"></a>傳回值

如果成功，則會使用[fegetround](fegetround-fesetround2.md)所報告的目前舍入格式，傳回*x*，四捨五入至最接近的整數。 否則，此函式可能會傳回下列其中一個值：

|問題|傳回|
|-----------|------------|
|*x* = ±無限大|±無限大、未修改|
|*x* = ±0|±0、未修改|
|*x* = NaN|NaN|

錯誤不會透過 [_matherr](matherr.md)回報。具體而言，此函數不會報告任何 **FE_INEXACT** 例外狀況。

## <a name="remarks"></a>備註

這個函式和 [rint](rint-rintf-rintl.md) 之間的主要差異在於，此函式不會引發不精確的浮點例外狀況。

因為最大浮點值是精確的整數，所以此函式自身永遠不會溢位；相反地，根據您使用的函式版本，輸出可能會造成傳回值溢位。

C + + 允許多載，所以您可以呼叫採用和傳回或參數的 **nearbyint** 多載 **`float`** **`long double`** 。 在 C 程式中，除非您使用 \<tgmath.h> 宏來呼叫這個函式，否則 **nearbyint** 一律會採用兩個雙精度值，並傳回雙精度浮點數。

如果您使用 \<tgmath.h> `nearbyint()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**nearbyint**、 **nearbyintf**、 **nearbyintl**|\<math.h>|\<cmath> 或 \<math.h>|
|**nearbyint** 宏 | \<tgmath.h> ||

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)<br/>
[數學與浮點支援](../floating-point-support.md)<br/>
