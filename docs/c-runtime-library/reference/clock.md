---
title: 時鐘
ms.date: 11/04/2016
api_name:
- clock
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
- clock
helpviewer_keywords:
- processor time used, calculating
- time, calculating processor
- clock function
- processor time used
- calculating processor time used
ms.assetid: 3e1853dd-498f-49ba-b06a-f2315f20904e
ms.openlocfilehash: 03d1a9ece92dbedfdceb89488e5d0440dc64f7ae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220726"
---
# <a name="clock"></a>時鐘

計算所呼叫的處理序使用的時鐘時間。

## <a name="syntax"></a>語法

```C
clock_t clock( void );
```

## <a name="return-value"></a>傳回值

從進程開始進行 CRT 初始化以來經過的時間，以每秒**CLOCKS_PER_SEC**單位來測量。 如果已耗用的時間無法使用，或已超過可記錄為**clock_t**類型的正時間上限，則此函式會傳回值 `(clock_t)(-1)` 。

## <a name="remarks"></a>備註

**Clock**函式會告訴在進程啟動期間，自 CRT 初始化之後已經過了多少時鐘時間。 請注意，此函式未完全符合將淨 CPU 時間指定為傳回值的 ISO C。 若要取得 CPU 時間，請使用 Win32 [GetProcessTimes](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getprocesstimes) 函式。 若要判斷經過的時間（以秒為單位），請將**clock**函數所傳回的值除以**CLOCKS_PER_SEC**的宏。

指定了足夠的時間，由**clock**傳回的值可能會超過**clock_t**的最大正數值。 當程式執行得更長時， **clock**所傳回的值一律為 `(clock_t)(-1)` ，如 iso C99 standard （7.23.2.1）和 iso C11 standard （7.27.2.1）所指定。 Microsoft 會將**clock_t**實作為 **`long`** 、帶正負號的32位整數，並將**CLOCKS_PER_SEC**巨集定義為1000。 這會提供最大的**時鐘**函數傳回值2147483.647 秒，或約24.8 天。 請勿依賴**時鐘**在執行超過此時間長度的進程中所傳回的值。 您可以使用64位[時間](time-time32-time64.md)函式或 Windows [QueryPerformanceCounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter)函數來記錄處理多年的已耗用時間。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**時鐘**|\<time.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_clock.c
// This sample uses clock() to 'sleep' for three
// seconds, then determines how long it takes
// to execute an empty loop 600000000 times.

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// Pauses for a specified number of clock cycles.
void do_sleep( clock_t wait )
{
   clock_t goal;
   goal = wait + clock();
   while( goal > clock() )
      ;
}

const long num_loops = 600000000L;

int main( void )
{
   long    i = num_loops;
   clock_t start, finish;
   double  duration;

   // Delay for a specified time.
   printf( "Delay for three seconds\n" );
   do_sleep( (clock_t)3 * CLOCKS_PER_SEC );
   printf( "Done!\n" );

   // Measure the duration of an event.
   start = clock();
   while( i-- )
      ;
   finish = clock();
   duration = (double)(finish - start) / CLOCKS_PER_SEC;
   printf( "Time to do %ld empty loops is ", num_loops );
   printf( "%2.3f seconds\n", duration );
}
```

```Output
Delay for three seconds
Done!
Time to do 600000000 empty loops is 1.354 seconds
```

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[difftime、_difftime32、_difftime64](difftime-difftime32-difftime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
