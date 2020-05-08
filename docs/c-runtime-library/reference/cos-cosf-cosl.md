---
title: cos、cosf、cosl
ms.date: 4/2/2020
api_name:
- cos
- cosf
- cosl
- _o_cos
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
- cos
- cosf
- cosl
helpviewer_keywords:
- cosines
- cosl function
- calculating cosine
- cosf function
- cos function
- trigonometric functions
- cosines, calculating
ms.assetid: ae90435e-6b68-4a47-a81f-be87d5c08f16
ms.openlocfilehash: 1aae123de5ef03af8bcaf8480a84327f88c457c5
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917235"
---
# <a name="cos-cosf-cosl"></a>cos、cosf、cosl

計算余弦值。

## <a name="syntax"></a>語法

```C
double cos( double x );
float cosf( float x );
long double cosl( long double x );
```

```cpp
float cos( float x );  // C++ only
long double cos( long double x );  // C++ only
```

### <a name="parameters"></a>參數

*x*<br/>
角度 (弧度)。

## <a name="return-value"></a>傳回值

*X*的余弦函數。 如果*x*大於或等於263，或小於或等於-263，則會在結果中失去重要性。

|輸入|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|± QNAN，IND|無|**_DOMAIN**|
|± INF|**無效**|**_DOMAIN**|

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用並傳回**float**或**long** **double**值的**cos**多載。 在 C 程式中， **cos**一律會採用並傳回**雙精度浮點數**。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的 C 標頭|必要的 C++ 標頭|
|-------------|---------------------|-|
|**cos**、 **cosh**、 **cosf**|\<math.h>|\<cmath> 或 \<math.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱[sin，sinf，sinl](sin-sinf-sinl.md)中的範例。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[acos、acosf、acosl](acos-acosf-acosl.md)<br/>
[asin、asinf、asinl](asin-asinf-asinl.md)<br/>
[atan、atanf、atanl、atan2、atan2f、atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[_matherr](matherr.md)<br/>
[sin、sinf、sinl](sin-sinf-sinl.md)<br/>
[tan、tanf、tanl](tan-tanf-tanl.md)<br/>
[_CIcos](../../c-runtime-library/cicos.md)<br/>
