---
title: abs、labs、llabs、_abs64 | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- abs
- _abs64
- labs
- llabs
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
- stdlib/_abs64
- math/abs
- _abs64
- abs
- labs
- math/labs
- llabs
- math/llabs
- cmath/abs
dev_langs:
- C++
helpviewer_keywords:
- absolute values
- abs function
- abs64 function
- _abs64 function
- calculating absolute values
ms.assetid: 60f789d1-4a1e-49f5-9e4e-0bdb277ea26a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc426bbbc28e6eb3b7e6e4a0fa9fab7e74f62093
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="abs-labs-llabs-abs64"></a>abs、labs、llabs、_abs64

計算引數的絕對值。

## <a name="syntax"></a>語法

```C
int abs( int n );
long labs( long n );
long long llabs( long long n );
__int64 _abs64( __int64 n );
```

```cpp
long abs( long n );   // C++ only
long long abs( long long n );   // C++ only
double abs( double n );   // C++ only
long double abs( long double n );   // C++ only
float abs( float n );   // C++ only
```

### <a name="parameters"></a>參數

*n*<br/>
數值。

## <a name="return-value"></a>傳回值

**Abs**，**實驗室**， **llabs**和 **_abs64**函式會傳回參數的絕對值*n*. 不會傳回錯誤。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫的多載**abs**採用並傳回**長**，**長****長**， **float**， **double**，和**長** **double**值。 這些多載是在 \<cmath> 標頭中定義。 在 C 程式中， **abs**一律採用並傳回 int。

**Microsoft 特定的**： 因為負數的整數，可以使用任何整數類資料類型表示的範圍超過可使用該類型表示的整數範圍，便可提供這些引數無法轉換的函式。 如果無法以傳回型別，表示引數的絕對值**abs**函式會傳回引數值不變。 具體來說，`abs(INT_MIN)`傳回**INT_MIN**，`labs(LONG_MIN)`傳回**LONG_MIN**，`llabs(LLONG_MIN)`傳回**LLONG_MIN**，和`_abs64(_I64_MIN)`傳回 **_I64_MIN**。 這表示**abs**函式無法用來保證正數值。

## <a name="requirements"></a>需求

|常式|必要的 C 標頭|必要的 C++ 標頭|
|-------------|-----------------------|---------------------------|
|**abs**，**實驗室**， **llabs**|\<math.h> 或 \<stdlib.h>|\<cmath>、\<cstdlib>、\<stdlib.h> 或 \<math.h>|
|**_abs64**|\<stdlib.h>|\<cstdlib> 或 \<stdlib.h>|

若要使用的多載的版本**abs**在 c + +，您必須包含\<h > 標頭。

## <a name="example"></a>範例

此程式會計算並顯示數個數字的絕對值。

```C
// crt_abs.c
// Build: cl /W3 /TC crt_abs.c
// This program demonstrates the use of the abs function
// by computing and displaying the absolute values of
// several numbers.

#include <stdio.h>
#include <math.h>
#include <stdlib.h>
#include <limits.h>

int main( void )
{
    int ix = -4;
    long lx = -41567L;
    long long llx = -9876543210LL;
    __int64 wx = -1;

    // absolute 32 bit integer value
    printf_s("The absolute value of %d is %d\n", ix, abs(ix));

    // absolute long integer value
    printf_s("The absolute value of %ld is %ld\n", lx, labs(lx));

    // absolute long long integer value
    printf_s("The absolute value of %lld is %lld\n", llx, llabs(llx));

    // absolute 64 bit integer value
    printf_s("The absolute value of 0x%.16I64x is 0x%.16I64x\n", wx,
        _abs64(wx));

    // Integer error cases:
    printf_s("Microsoft implementation-specific results:\n");
    printf_s(" abs(INT_MIN) returns %d\n", abs(INT_MIN));
    printf_s(" labs(LONG_MIN) returns %ld\n", labs(LONG_MIN));
    printf_s(" llabs(LLONG_MIN) returns %lld\n", llabs(LLONG_MIN));
    printf_s(" _abs64(_I64_MIN) returns 0x%.16I64x\n", _abs64(_I64_MIN));
}
```

```Output
The absolute value of -4 is 4
The absolute value of -41567 is 41567
The absolute value of -9876543210 is 9876543210
The absolute value of 0xffffffffffffffff is 0x0000000000000001
Microsoft implementation-specific results:
abs(INT_MIN) returns -2147483648
labs(LONG_MIN) returns -2147483648
llabs(LLONG_MIN) returns -9223372036854775808
_abs64(_I64_MIN) returns 0x8000000000000000
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[_cabs](cabs.md)<br/>
[fabs、fabsf、fabsl](fabs-fabsf-fabsl.md)<br/>
[imaxabs](imaxabs.md)<br/>
