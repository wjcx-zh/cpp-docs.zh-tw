---
title: difftime、_difftime32、_difftime64
ms.date: 11/04/2016
api_name:
- _difftime32
- difftime
- _difftime64
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
- api-ms-win-crt-time-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _difftime64
- difftime
- difftime64
- _difftime32
- difftime32
helpviewer_keywords:
- _difftime32 function
- difftime function
- time, finding the difference
- difftime64 function
- _difftime64 function
- difftime32 function
ms.assetid: 4cc0ac2b-fc7b-42c0-8283-8c9d10c566d0
ms.openlocfilehash: 51d74ae447e87e91e9be3c27864b8dfe7f490b14
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937637"
---
# <a name="difftime-_difftime32-_difftime64"></a>difftime、_difftime32、_difftime64

求得兩個時間的差。

## <a name="syntax"></a>語法

```C
double difftime( time_t timeEnd, time_t timeStart );
double _difftime32( __time32_t timeEnd, __time32_t timeStart );
double _difftime64( __time64_t timeEnd, __time64_t timeStart );
```

### <a name="parameters"></a>參數

*timeEnd*<br/>
結束時間。

*timeStart*<br/>
開始時間。

## <a name="return-value"></a>傳回值

**difftime**會傳回從*timeStart*到*timeEnd*的經過時間（以秒為單位）。 傳回的值是雙精度浮點數。 傳回的值可能是 0，表示有錯誤。

## <a name="remarks"></a>備註

**Difftime**函數會計算兩個提供的時間值之間的差異*timeStart*和*timeEnd*。

提供的時間值必須符合**time_t**的範圍。 **time_t**是64位的值。 因此，範圍的結束時間已從 2038 年 1 月 18 日 23:59:59 (UTC) 延長到 3000 年 12 月 31 日 23:59:59。 較低的**time_t**範圍仍然是1970年1月1日午夜。

**difftime**是一個內嵌函式，會根據是否已定義 **_USE_32BIT_TIME_T** ，評估為 **_difftime32**或 **_difftime64** 。 _difftime32 和 _difftime64 可用來直接強制使用特定大小的時間類型。

這些函式會驗證它們的參數。 如果任一參數為零或負數，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回0，並將**errno**設為**EINVAL**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**difftime**|\<time.h>|
|**_difftime32**|\<time.h>|
|**_difftime64**|\<time.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```cpp
// crt_difftime.c
// This program calculates the amount of time
// needed to do a floating-point multiply 100 million times.
//

#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <float.h>

double RangedRand( float range_min, float range_max)
{
   // Generate random numbers in the half-closed interval
   // [range_min, range_max). In other words,
   // range_min <= random number < range_max
   return ((double)rand() / (RAND_MAX + 1) * (range_max - range_min)
            + range_min);
}

int main( void )
{
   time_t   start, finish;
   long     loop;
   double   result, elapsed_time;
   double   arNums[3];

   // Seed the random-number generator with the current time so that
   // the numbers will be different every time we run.
   srand( (unsigned)time( NULL ) );

   arNums[0] = RangedRand(1, FLT_MAX);
   arNums[1] = RangedRand(1, FLT_MAX);
   arNums[2] = RangedRand(1, FLT_MAX);
   printf( "Using floating point numbers %.5e %.5e %.5e\n", arNums[0], arNums[1], arNums[2] );

   printf( "Multiplying 2 numbers 100 million times...\n" );

   time( &start );
   for( loop = 0; loop < 100000000; loop++ )
      result = arNums[loop%3] * arNums[(loop+1)%3];
   time( &finish );

   elapsed_time = difftime( finish, start );
   printf( "\nProgram takes %6.0f seconds.\n", elapsed_time );
}
```

```Output
Using random floating point numbers 1.04749e+038 2.01482e+038 1.72737e+038
Multiplying 2 floating point numbers 100 million times...
Program takes      3 seconds.
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[時間管理](../../c-runtime-library/time-management.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
