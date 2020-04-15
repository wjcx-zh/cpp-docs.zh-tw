---
title: _ftime_s、_ftime32_s、_ftime64_s
ms.date: 4/2/2020
api_name:
- _ftime_s
- _ftime64_s
- _ftime32_s
- _o__ftime32_s
- _o__ftime64_s
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ftime_s
- _ftime64_s
- ftime_s
- _ftime32_s
- ftime32_s
- ftime64_s
helpviewer_keywords:
- ftime32_s function
- ftime_s function
- _ftime64_s function
- current time
- ftime64_s function
- time, getting current
- _ftime_s function
- _ftime32_s function
ms.assetid: d03080d9-a520-45be-aa65-504bdb197e8b
ms.openlocfilehash: 0ffd779d8c74b64403837bd973b025da7e3fac2b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345559"
---
# <a name="_ftime_s-_ftime32_s-_ftime64_s"></a>_ftime_s、_ftime32_s、_ftime64_s

取得目前時間。 這些是具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md) 版本。

## <a name="syntax"></a>語法

```C
errno_t _ftime_s( struct _timeb *timeptr );
errno_t _ftime32_s( struct __timeb32 *timeptr );
errno_t _ftime64_s( struct __timeb64 *timeptr );
```

### <a name="parameters"></a>參數

*timeptr*<br/>
指向 **_timeb、__timeb32****__timeb32**或 **__timeb64**結構的指標。

## <a name="return-value"></a>傳回值

如果成功，則為零，如果失敗，則為錯誤碼。 如果*時間點*為**NULL,** 則傳回值為**EINVAL**。

## <a name="remarks"></a>備註

**_ftime_s**函數獲取當前本地時間並將其存儲在*timeptr*指向的結構中。 **_timeb、__timeb32**和 **__timeb64**結構在 SYS_Timeb.h **__timeb32**中定義。 它們包含下表中所列出的四個欄位。

|欄位|描述|
|-|-|
|**德斯特弗拉格**|若日光節約時間目前於本地時區已生效，則為非零。 (如需如何判斷日光節約時間的說明，請參閱 [_tzset](tzset.md)。)|
|**米裡特姆**|秒數的分數，以毫秒為單位。|
|**time**|自國際標準時間 (UTC) 1970 年 1 月 1 日午夜 (00:00:00) 以來的時間，以秒為單位。|
|**timezone**|UTC 和當地時間之間的時差，向西推進，以分鐘為單位。 **時區**的值是從全域變數 **_timezone**的值設置的(請參閱 **_tzset**)。|

_ftime64_s**函數**使用 **__timeb64**結構,允許文件創建日期在 UTC 12 月 31 日 23:59:59 之前表示;而 **_ftime32_s**僅表示 2038 年 1 月 18 日 23:59:59,UTC 的日期。 1970 年 1 月 1 日午夜是所有這些函式的日期範圍下限。

**_ftime_s**函數等效於 **_ftime64_s**,**並且_timeb**包含 64 位元時間,除非定義了 **_USE_32BIT_TIME_T,** 在這種情況下,舊行為有效;**_ftime_s**使用 32 位時間 **,_timeb**包含 32 位元時間。

**_ftime_s**驗證其參數。 如果將空指標傳遞為*timeptr,* 則函數將呼叫無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則函數將**errno**設定到**EINVAL**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**_ftime_s**|\<sys/types.h> 和 \<sys/timeb.h>|
|**_ftime32_s**|\<sys/types.h> 和 \<sys/timeb.h>|
|**_ftime64_s**|\<sys/types.h> 和 \<sys/timeb.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_ftime64_s.c
// This program uses _ftime64_s to obtain the current
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

   _ftime64_s( &timebuffer );

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
