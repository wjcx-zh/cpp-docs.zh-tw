---
title: div、ldiv、lldiv
ms.date: 04/05/2018
api_name:
- div
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
- api-ms-win-crt-utility-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- div
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
ms.openlocfilehash: 5b40fa0c4cc9cdf0c0de0f6af21da04b0c70369f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937688"
---
# <a name="div-ldiv-lldiv"></a>div、ldiv、lldiv

計算兩個整數值的商數和餘數。

## <a name="syntax"></a>語法

```C
div_t div(
   int numer,
   int denom
);
ldiv_t ldiv(
   long numer,
   long denom
);
lldiv_t lldiv(
   long long numer,
   long long denom
);
```

```cpp
ldiv_t div(
   long numer,
   long denom
); /* C++ only */
lldiv_t div(
   long long numer,
   long long denom
); /* C++ only */
```

### <a name="parameters"></a>參數

*推*<br/>
分子。

*denom*<br/>
分母。

## <a name="return-value"></a>傳回值

使用**int**類型的引數呼叫的**div**會傳回**div_t**類型的結構，其中包含商和餘數。 具有**long**類型之引數的傳回值是**ldiv_t**，而具有**long** **long 類型**之引數的傳回值則是**lldiv_t**。 **div_t**、 **ldiv_t**和**lldiv_t**都是在 stdlib.h> \<中定義 >。

## <a name="remarks"></a>備註

**Div**函式會將*推*除以*denom* ，因此會計算商和餘數。 [Div_t](../../c-runtime-library/standard-types.md)結構包含**商、...** 和餘數， **rem**。商數的正負號與數學商數相同。 其絕對值是小於數學商數絕對值的最大整數。 如果分母為 0，程式會終止並出現錯誤訊息。

接受**long**或**long**類型之引數的**div**多載僅適用于C++程式碼。 傳回類型[ldiv_t](../../c-runtime-library/standard-types.md)和[lldiv_t](../../c-runtime-library/standard-types.md)包含與**div_t**的成員相同**的成員。**

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**div**、 **ldiv**、 **lldiv**|\<stdlib.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_div.c
// arguments: 876 13

// This example takes two integers as command-line
// arguments and displays the results of the integer
// division. This program accepts two arguments on the
// command line following the program name, then calls
// div to divide the first argument by the second.
// Finally, it prints the structure members quot and rem.
//

#include <stdlib.h>
#include <stdio.h>
#include <math.h>

int main( int argc, char *argv[] )
{
   int x,y;
   div_t div_result;

   x = atoi( argv[1] );
   y = atoi( argv[2] );

   printf( "x is %d, y is %d\n", x, y );
   div_result = div( x, y );
   printf( "The quotient is %d, and the remainder is %d\n",
           div_result.quot, div_result.rem );
}
```

```Output
x is 876, y is 13
The quotient is 67, and the remainder is 5
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv、lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
