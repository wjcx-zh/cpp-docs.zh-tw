---
title: 時鐘
ms.date: 11/04/2016
apiname:
- clock
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- clock
helpviewer_keywords:
- processor time used, calculating
- time, calculating processor
- clock function
- processor time used
- calculating processor time used
ms.assetid: 3e1853dd-498f-49ba-b06a-f2315f20904e
ms.openlocfilehash: 4b58b33b533250447cf964134de9869bddee4498
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492616"
---
# <a name="clock"></a>時鐘

計算所呼叫的處理序使用的時鐘時間。

## <a name="syntax"></a>語法

```C
clock_t clock( void );
```

## <a name="return-value"></a>傳回值

CRT 初始化在開始處理序之後, 經過的時間測量單位**CLOCKS_PER_SEC**每秒的單位。 如果已耗用時間無法使用或已超過可記錄為最大正時間**clock_t 要求**類型，此函式會傳回值`(clock_t)(-1)`。

## <a name="remarks"></a>備註

**時鐘**函式會告訴 CRT 初始化程序啟動期間過多少時鐘時間。 請注意，此函式未完全符合將淨 CPU 時間指定為傳回值的 ISO C。 若要取得 CPU 時間，請使用 Win32 [GetProcessTimes](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getprocesstimes) 函式。 若要判斷經過的時間，以秒為單位，將分割所傳回的值**時鐘**函式巨集所**CLOCKS_PER_SEC**。

有足夠的時間，所傳回的值**時鐘**可能會超過最大正值**clock_t 要求**。 當執行程序更久，所傳回的值**時鐘**總是`(clock_t)(-1)`、 ISO C99 標準 (7.23.2.1) 和 ISO C11 標準 (7.27.2.1) 所指定。 Microsoft 實作**clock_t 要求**作為**長**，32 位元帶正負號的整數，而**CLOCKS_PER_SEC**巨集定義為 1000年。 這可提供最多**時鐘**函式傳回值 2147483.647 秒，或大約 24.8 天。 所傳回的值並不依賴**時鐘**已執行超過這段時間的處理序中。 您可以使用 64 位元[時間](time-time32-time64.md)函式或 Windows [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904)多年來的記錄處理序已耗用時間的函式。

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

// Pauses for a specified number of milliseconds.
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
