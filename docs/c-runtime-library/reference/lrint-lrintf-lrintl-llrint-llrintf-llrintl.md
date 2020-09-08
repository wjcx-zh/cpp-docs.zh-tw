---
title: lrint、lrintf、lrintl、llrint、llrintf、llrintl
description: 'Lrint 的 API 參考 ( # A1、lrintf ( # A3、lrintl ( # A5、llrint ( # A7、llrintf ( # A9 和 llrintl ( # A11;這會使用目前的舍入模式和方向，將指定的浮點值四捨五入為最接近的整數值。'
ms.date: 9/1/2020
api_name:
- lrint
- lrintl
- lrintf
- llrint
- llrintf
- llrintl
- _o_llrint
- _o_llrintf
- _o_llrintl
- _o_lrint
- _o_lrintf
- _o_lrintl
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
- lrint
- lrintf
- lrintl
- llrint
- llrintf
- llrintl
- math/lrint
- math/lrintf
- math/lrintl
- math/llrint
- math/llrintf
- math/llrintl
helpviewer_keywords:
- lrint function
- lrintf function
- lrintl function
- llrint function
- llrintf function
- llrintl function
ms.assetid: 28ccd5b3-5e6f-434f-997d-a21d51b8ce7f
ms.openlocfilehash: f208c183400aac7a110bb6fd87398d4377fe8f06
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555016"
---
# <a name="lrint-lrintf-lrintl-llrint-llrintf-llrintl"></a>lrint、lrintf、lrintl、llrint、llrintf、llrintl

使用目前的進位模式和方向，將指定的浮點值四捨五入成最接近的整數值。

## <a name="syntax"></a>語法

```C
long int lrint(
   double x
);

long int lrint(
   float x
); //C++ only

long int lrint(
   long double x
); //C++ only

long int lrintf(
   float x
);

long int lrintl(
   long double x
);

long long int llrint(
   double x
);

long long int llrint(
   float x
); //C++ only

long long int llrint(
   long double x
); //C++ only

long long int llrintf(
   float x
);

long long int llrintl(
   long double x
);

#define lrint(X) // Requires C11 or higher
```

### <a name="parameters"></a>參數

*X*\
要捨入的值。

## <a name="return-value"></a>傳回值

如果成功，則傳回 *x*的舍入整數值。

|問題|傳回|
|-----------|------------|
|*x* 超出傳回型別的範圍<br /><br /> *x* = ±∞<br /><br /> *x* = NaN|引發 **FE_INVALID** ，並傳回零 (0) 。|

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用和類型之 **lrint** 和 **llrint** 的多載 **`float`** **`long double`** 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **lrint** 和 **llrint** 一律會採用 **`double`** 。

如果您使用 \<tgmath.h> `llrint()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

如果 *x* 不是整數值的相等浮點數，這些函數會引發 **FE_INEXACT**。

**Microsoft 特定**：當結果超出傳回型別的範圍，或是當參數為 NaN 或無限大時，傳回值就會定義為實值。 Microsoft 編譯器會傳回零 (0) 值。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**lrint**、 **lrintf**、 **lrintl**、 **llrint**、 **llrintf**、 **llrintl**|\<math.h>|\<cmath>|
|**lrint** 宏 | \<tgmath.h> ||

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)
