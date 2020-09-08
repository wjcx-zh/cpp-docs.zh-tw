---
title: asin、asinf、asinl
description: Asin、asinf 和 asinl 的 API 參考;計算浮點值的反正弦值。
ms.date: 08/31/2020
api_name:
- asinf
- asinl
- asin
- _o_asin
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
- asin
- asinl
- asinf
helpviewer_keywords:
- asin function
- asinl function
- asinf function
- trigonometric functions
- arcsine function
ms.assetid: ca05f9ea-b711-49f6-9f32-2f4019abfd69
ms.openlocfilehash: 7167debcfb605ab05720d9441943439ea9982324
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556654"
---
# <a name="asin-asinf-asinl"></a>asin、asinf、asinl

計算反正弦值。

## <a name="syntax"></a>語法

```C
double asin( double x );
float asinf ( float x );
long double asinl( long double x );
#define asin(X) // Requires C11 or higher

float asin( float x );  // C++ only
long double asin( long double x );  // C++ only
```

### <a name="parameters"></a>參數

*X*\
要計算的反正弦值。

## <a name="return-value"></a>傳回值

**Asin**函式會傳回反正弦函數 (反正弦函數) *x* ，範圍介於-π/2 到π/2 弧度之間。

依預設，如果 *x* 小於-1 或大於1， **asin** 會傳回不定。

|輸入|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|± ∞|**無效**|**_DOMAIN**|
|± **QNAN**、 **IND**|無|**_DOMAIN**|
|&#124;x&#124;>1|**無效**|**_DOMAIN**|

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以使用和值來呼叫 **asin** 的多載 **`float`** **`long double`** 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **asin** 一律會採用並傳回 **`double`** 。

如果您使用 \<tgmath.h> `asin()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭 (C)|必要的標頭 (C++)|
|-------------|---------------------|-|
|**asin**、 **asinf**、 **asinl**|\<math.h>|\<cmath> 或 \<math.h>|
|**asin ( # B1 ** 宏 | \<tgmath.h> ||

## <a name="example"></a>範例

如需詳細資訊，請參閱 [acos、acosf、acosl](acos-acosf-acosl.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[acos、acosf、acosl](acos-acosf-acosl.md)<br/>
[atan、atanf、atanl、atan2、atan2f、atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos、cosf、cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin、sinf、sinl](sin-sinf-sinl.md)<br/>
[tan、tanf、tanl](tan-tanf-tanl.md)<br/>
