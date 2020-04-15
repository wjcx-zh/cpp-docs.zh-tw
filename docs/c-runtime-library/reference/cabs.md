---
title: _cabs
ms.date: 4/2/2020
api_name:
- _cabs
- _o__cabs
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: e77e1811cb6f002c06e514b5f737b8a92ea84282
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333684"
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

*Z*<br/>
複數。

## <a name="return-value"></a>傳回值

**_cabs**返回其參數的絕對值(如果成功)。 在溢出時 **,_cabs**傳回**HUGE_VAL**並將**errno**設定到**ERANGE**。 您可以使用 [_matherr](matherr.md) 變更錯誤處理。

## <a name="remarks"></a>備註

**_cabs**函數計算複數的絕對值,該值必須是[類型_complex](../../c-runtime-library/standard-types.md)的結構。 結構*z*由實際元件*x*和虛部分量*y*組成。 對 **_cabs**的調用生成一個等效於`sqrt( z.x * z.x + z.y * z.y )`表達式的值。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_cabs**|\<math.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

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
