---
title: round、roundf、roundl
description: Round、roundf 和 roundl 的 API 參考;這會將浮點值四捨五入為最接近的整數值。
ms.date: 09/25/2020
api_name:
- round
- roundl
- roundf
- _o_round
- _o_roundf
- _o_roundl
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
- roundf
- roundl
- round
helpviewer_keywords:
- roundl function
- round function
- roundf function
ms.assetid: 6be90877-193c-4b80-a32b-c3eca33f9c6f
ms.openlocfilehash: 2e51eb375ab814119dcf34d85c7f5aff11559784
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499173"
---
# <a name="round-roundf-roundl"></a>round、roundf、roundl

將浮點值四捨五入為最接近的整數值。

## <a name="syntax"></a>語法

```C
double round(
   double x
);
float round(
   float x
);  // C++ only
long double round(
   long double x
);  // C++ only
float roundf(
   float x
);
long double roundl(
   long double x
);
#define round(X) // Requires C11 or higher
```

### <a name="parameters"></a>參數

*X*\
要四捨五入的浮點值。

## <a name="return-value"></a>傳回值

**Round**函式會傳回浮點值，表示最接近*x*的整數。 不論浮點進位模式設定為何，中間值都會背離零四捨五入。 不會傳回錯誤。

|輸入|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|± **QNAN**、 **IND**|無|**_DOMAIN**|

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫 take 和 return 和值的 **round** 多載 **`float`** **`long double`** 。 在 C 程式中，除非您使用 \<tgmath.h> 宏來呼叫這個函式，否則 **round** 一律會採用並傳回 **`double`** 。

如果您使用 \<tgmath.h> `round()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**round**、 **roundf**、 **roundl**|\<math.h>|
|**round** 宏 | \<tgmath.h> ||

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// Build with: cl /W3 /Tc
// This example displays the rounded
// results of floating-point values

#include <math.h>
#include <stdio.h>

int main()
{
    printf("===== Round a float\n\n");
    float floatValue = 2.4999999f; // float stores a value close to, but not exactly equal to, the initializer below. floatValue will contain 2.5 because it is the closest single precision value
    printf("roundf(%.1000g) is %.1000g\n", floatValue, roundf(floatValue));
    printf("roundf(%.1000g) is %.1000g\n", -floatValue, roundf(-floatValue));

    // double stores a value close to, but not exactly equal to, the initializer below. The closest double value is just slightly larger.
    double doubleValue = 2.4999999;
    printf("\n===== Round a double\n\n");
    printf("round(%.1000g) is %.1000g\n", doubleValue, round(doubleValue));
    printf("round(%.1000g) is %.1000g\n", -doubleValue, round(-doubleValue));

    // long double stores a value close to, but not exactly equal to, the initializer below. The closest long double value is just slightly larger.
    long double longDoubleValue = 2.4999999L;
    printf("\n===== Round a long double\n\n");
    printf("roundl(%.1000g) is %.1000g\n", longDoubleValue, roundl(longDoubleValue));
    printf("roundl(%.1000g) is %.1000g\n", -longDoubleValue, roundl(-longDoubleValue));

    return 0;
}
```

```Output
===== Round a float

roundf(2.5) is 3
roundf(-2.5) is -3

===== Round a double

round(2.499999900000000163657887242152355611324310302734375) is 2
round(-2.499999900000000163657887242152355611324310302734375) is -2

===== Round a long double

roundl(2.499999900000000163657887242152355611324310302734375) is 2
roundl(-2.499999900000000163657887242152355611324310302734375) is -2
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)\
[ceil、ceilf、ceill](ceil-ceilf-ceill.md)\
[floor、floorf、floorl](floor-floorf-floorl.md)\
[fmod、fmodf](fmod-fmodf.md)\
[lrint、lrintf、lrintl、llrint、llrintf、llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)\
[lround、lroundf、lroundl、llround、llroundf、llroundl](lround-lroundf-lroundl-llround-llroundf-llroundl.md)\
[nearbyint、nearbyintf、nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)\
[rint、rintf、rintl](rint-rintf-rintl.md)
