---
title: __min
ms.date: 04/05/2018
api_name:
- __min
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __min
- min
- _min
helpviewer_keywords:
- __min macro
- min macro
- minimum macro
- _min macro
ms.assetid: 2037f26c-b48a-4a69-8870-22519f052a3c
ms.openlocfilehash: 6b5cc6517c125f91337ca0d9b12b7a49bd7c1753
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951728"
---
# <a name="__min"></a>__min

預處理器宏，會傳回兩個值中較小的一個。

## <a name="syntax"></a>語法

```C
#define __min(a,b) (((a) < (b)) ? (a) : (b))
```

### <a name="parameters"></a>參數

*a*、 *b*<br/>
運算子所 **<** 處理之任何類型的值。

## <a name="return-value"></a>傳回值

兩個引數的較小引數。

## <a name="remarks"></a>備註

**__Min**宏會比較兩個值，並傳回較小的值。 引數可以是帶正負號或不帶正負號的任何數值資料類型。 引數和傳回值必須屬於相同的資料類型。

傳回的引數會透過宏進行兩次評估。 如果引數是在評估時改變其值的運算式（例如`*p++`），這可能會導致非預期的結果。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**__min**|\<stdlib.h>|

## <a name="example"></a>範例

```C
// crt_minmax.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int a = 10;
   int b = 21;

   printf( "The larger of %d and %d is %d\n",  a, b, __max( a, b ) );
   printf( "The smaller of %d and %d is %d\n", a, b, __min( a, b ) );
}
```

```Output
The larger of 10 and 21 is 21
The smaller of 10 and 21 is 10
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[__max](max.md)<br/>
