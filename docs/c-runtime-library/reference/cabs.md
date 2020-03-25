---
title: _cabs
ms.date: 11/04/2016
api_name:
- _cabs
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
- _cabs
helpviewer_keywords:
- cabs function
- absolute values
- _cabs function
- calculating absolute values
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
ms.openlocfilehash: 2c2bd6b3f097095514e47b757306b4d83a990e45
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170337"
---
# <a name="_cabs"></a>_cabs

計算複數的絕對值。

## <a name="syntax"></a>語法

```C
double _cabs(
   struct _complex z
);
```

### <a name="parameters"></a>參數

*z*<br/>
複數。

## <a name="return-value"></a>傳回值

如果成功， **_cabs**會傳回其引數的絕對值。 溢位時， **_cabs**會傳回**HUGE_VAL** ，並將**errno**設定為**ERANGE**。 您可以使用 [_matherr](matherr.md) 變更錯誤處理。

## <a name="remarks"></a>備註

**_Cabs**函式會計算複數的絕對值，此數值必須是[_complex](../../c-runtime-library/standard-types.md)類型的結構。 結構*z*是由實陣列件*x*和虛陣列件*y*所組成。 **_Cabs**的呼叫會產生相當於運算式 `sqrt( z.x * z.x + z.y * z.y )`的值。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_cabs**|\<math.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_cabs.c
// Using _cabs, this program calculates
// the absolute value of a complex number.

#include <math.h>
#include <stdio.h>

int main( void )
{
   struct _complex number = { 3.0, 4.0 };
   double d;

   d = _cabs( number );
   printf( "The absolute value of %f + %fi is %f\n",
           number.x, number.y, d );
}
```

```Output
The absolute value of 3.000000 + 4.000000i is 5.000000
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[abs、labs、llabs、_abs64](abs-labs-llabs-abs64.md)<br/>
[fabs、fabsf、fabsl](fabs-fabsf-fabsl.md)
