---
title: _ftime、_ftime32、_ftime64
ms.date: 11/04/2016
apiname:
- _ftime64
- _ftime
- _ftime32
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
- _ftime32
- _ftime
- _ftime64
- ftime64
- ftime
- ftime32
helpviewer_keywords:
- ftime64 function
- _ftime64 function
- current time
- _ftime function
- ftime function
- _ftime32 function
- ftime32 function
- time, getting current
ms.assetid: 96bc464c-3bcd-41d5-a212-8bbd836b814a
ms.openlocfilehash: 26178f8e559bddd3dafb7fa21edb822874244e93
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508325"
---
# <a name="ftime-ftime32-ftime64"></a>_ftime、_ftime32、_ftime64

取得目前時間。 這些函式有更安全的版本可供使用，請參閱 [_ftime_s、_ftime32_s、_ftime64_s](ftime-s-ftime32-s-ftime64-s.md)。

## <a name="syntax"></a>語法

```C
void _ftime( struct _timeb *timeptr );
void _ftime32( struct __timeb32 *timeptr );
void _ftime64( struct __timeb64 *timeptr );
```

### <a name="parameters"></a>參數

*timeptr*<br/>
指標 **_timeb**， **__timeb32**，或 **__timeb64**結構。

## <a name="remarks"></a>備註

**_Ftime**函式取得目前的當地時間，並將它儲存在結構中所指*timeptr*。 **_Timeb**， **__timeb32**，並 **__timeb64**中所定義的結構\<sys\\timeb.h >。 它們包含下表中所列出的四個欄位。

|欄位|描述|
|-|-|
|**dstflag**|若日光節約時間目前於本地時區已生效，則為非零。 (如需如何判斷日光節約時間的說明，請參閱 [_tzset](tzset.md)。)|
|**millitm**|秒數的分數，以毫秒為單位。|
|**time**|自國際標準時間 (UTC) 1970 年 1 月 1 日午夜 (00:00:00) 以來的時間，以秒為單位。|
|**timezone**|UTC 和當地時間之間的時差，向西推進，以分鐘為單位。 值**時區**會設定全域變數的值從 **_timezone** (請參閱 **_tzset**)。|

**_Ftime64**函式，以使用 **__timeb64**結構，可讓檔案建立日期最高表示為 23:59:59，3000 年 12 月 31 日 UTC; 而 **_ftime32**僅代表到 23:59:59 2038 年 1 月 18 日 UTC 的日期。 1970 年 1 月 1 日午夜是所有這些函式的日期範圍下限。

**_Ftime**函式相當於 **_ftime64**，並 **_timeb**包含 64 位元時間，除非 **_USE_32BIT_TIME_T**定義，在這種情況下的舊的行為就會生效;**_ftime**會使用 32 位元時間並 **_timeb**包含 32 位元時間。

**_ftime**會驗證其參數。 如果傳遞 null 做為指標*timeptr*，函式會叫用無效參數處理常式，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，則函式會設定**errno**要**EINVAL**。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**_ftime**|\<sys/types.h> 和 \<sys/timeb.h>|
|**_ftime32**|\<sys/types.h> 和 \<sys/timeb.h>|
|**_ftime64**|\<sys/types.h> 和 \<sys/timeb.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_ftime.c
// compile with: /W3
// This program uses _ftime to obtain the current
// time and then stores this time in timebuffer.

#include <stdio.h>
#include <sys/timeb.h>
#include <time.h>

int main( void )
{
   struct _timeb timebuffer;
   char timeline[26];
   errno_t err;
   time_t time1;
   unsigned short millitm1;
   short timezone1;
   short dstflag1;

   _ftime( &timebuffer ); // C4996
   // Note: _ftime is deprecated; consider using _ftime_s instead

   time1 = timebuffer.time;
   millitm1 = timebuffer.millitm;
   timezone1 = timebuffer.timezone;
   dstflag1 = timebuffer.dstflag;

   printf( "Seconds since midnight, January 1, 1970 (UTC): %I64d\n",
   time1);
   printf( "Milliseconds: %d\n", millitm1);
   printf( "Minutes between UTC and local time: %d\n", timezone1);
   printf( "Daylight savings time flag (1 means Daylight time is in "
           "effect): %d\n", dstflag1);

   err = ctime_s( timeline, 26, & ( timebuffer.time ) );
   if (err)
   {
       printf("Invalid argument to ctime_s. ");
   }
   printf( "The time is %.19s.%hu %s", timeline, timebuffer.millitm,
           &timeline[20] );
}
```

```Output
Seconds since midnight, January 1, 1970 (UTC): 1051553334
Milliseconds: 230
Minutes between UTC and local time: 480
Daylight savings time flag (1 means Daylight time is in effect): 1
The time is Mon Apr 28 11:08:54.230 2003
```

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
