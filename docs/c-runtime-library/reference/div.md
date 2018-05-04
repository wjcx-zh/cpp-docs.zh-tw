---
title: div ldiv、 lldiv |Microsoft 文件
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- div
apilocation:
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
apitype: DLLExport
f1_keywords:
- div
dev_langs:
- C++
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ba1625105adf6edbc6419bd4fdabc8bda5d0e98
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="div-ldiv-lldiv"></a>div ldiv、 lldiv

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

*numer*<br/>
分子。

*denom*<br/>
分母。

## <a name="return-value"></a>傳回值

**div**使用類型引數呼叫**int**傳回型別的結構**div_t**，其中包括商數及餘數。 傳回值的型別引數**長**是**ldiv_t**，和傳回值的型別引數與**長****長**是**lldiv_t**。 **div_t**， **ldiv_t**，和**lldiv_t**中定義\<stdlib.h >。

## <a name="remarks"></a>備註

**Div**函式除以*numer*由*denom* ，並藉此計算商數及餘數。 [Div_t](../../c-runtime-library/standard-types.md)結構包含商數**q u o t**，其餘部分，及**rem**。商數的正負號與數學商數相同。 其絕對值是小於數學商數絕對值的最大整數。 如果分母為 0，程式會終止並出現錯誤訊息。

多載**div**可接受類型引數**長**或**長****長**才可以使用 c + + 程式碼。 傳回型別[ldiv_t](../../c-runtime-library/standard-types.md)和[lldiv_t](../../c-runtime-library/standard-types.md)包含成員**q u o t**和**rem**，其中具有相同意義為成員**div_t**。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**div**， **ldiv**， **lldiv**|\<stdlib.h>|

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
