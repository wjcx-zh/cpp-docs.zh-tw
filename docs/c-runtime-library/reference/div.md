---
title: div、 ldiv、 lldiv
ms.date: 04/05/2018
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
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
ms.openlocfilehash: 0ee1b3b6a5d7b15470ffe1e667b4077d1f9581e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339256"
---
# <a name="div-ldiv-lldiv"></a>div、 ldiv、 lldiv

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

**div**使用的型別引數呼叫**int**會傳回類型的結構**div_t**，其中包括商數和餘數。 傳回值與類型的引數**長**是**ldiv_t**，和傳回值的型別引數**長****長**是**lldiv_t**。 **div_t**， **ldiv_t**，以及**lldiv_t**中所定義\<stdlib.h >。

## <a name="remarks"></a>備註

**Div**函式除以*號碼*由*denom* ，並藉此計算商數和餘數。 [Div_t](../../c-runtime-library/standard-types.md)結構包含商數**q u o t**，和餘數**rem**。商數的正負號與數學商數相同。 其絕對值是小於數學商數絕對值的最大整數。 如果分母為 0，程式會終止並出現錯誤訊息。

多載**div**可接受類型引數**長**或**長****長**而僅適用於C++的程式碼。 傳回型別[ldiv_t](../../c-runtime-library/standard-types.md)並[lldiv_t](../../c-runtime-library/standard-types.md)包含成員**q u o t**並**rem**，其中具有相同意義隸屬**div_t**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
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
