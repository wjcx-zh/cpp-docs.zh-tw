---
title: _ftime_s、_ftime32_s、_ftime64_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _ftime_s
- _ftime64_s
- _ftime32_s
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
- _ftime_s
- _ftime64_s
- ftime_s
- _ftime32_s
- ftime32_s
- ftime64_s
dev_langs:
- C++
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
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e69b066f9dfec420155631c4f31a1cc97750ea72
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="ftimes-ftime32s-ftime64s"></a>_ftime_s、_ftime32_s、_ftime64_s

取得目前時間。 這些是具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md) 版本。

## <a name="syntax"></a>語法

```C
errno_t _ftime_s( struct _timeb *timeptr );
errno_t _ftime32_s( struct __timeb32 *timeptr );
errno_t _ftime64_s( struct __timeb64 *timeptr );
```

### <a name="parameters"></a>參數

*timeptr*<br/>
指標 **_timeb**， **__timeb32**，或 **__timeb64**結構。

## <a name="return-value"></a>傳回值

如果成功，則為零，如果失敗，則為錯誤碼。 如果*timeptr*是**NULL**，則傳回值是**EINVAL**。

## <a name="remarks"></a>備註

**_Ftime_s**函式取得目前的當地時間，並將它儲存在結構中所指*timeptr*。 **_Timeb**， **__timeb32**，和 **__timeb64** SYS\Timeb.h 中所定義的結構。 它們包含下表中所列出的四個欄位。

|欄位|描述|
|-|-|
|**dstflag**|若日光節約時間目前於本地時區已生效，則為非零。 (如需如何判斷日光節約時間的說明，請參閱 [_tzset](tzset.md)。)|
|**millitm**|秒數的分數，以毫秒為單位。|
|**time**|自國際標準時間 (UTC) 1970 年 1 月 1 日午夜 (00:00:00) 以來的時間，以秒為單位。|
|**timezone**|UTC 和當地時間之間的時差，向西推進，以分鐘為單位。 值**時區**從全域變數的值會設定 **_timezone** (請參閱 **_tzset**)。|

**_Ftime64_s**函式，以使用 **__timeb64**結構時，請允許檔案建立日期，以透過 23:59:59，3000 年 12 月 31 日 UTC; 設定來表示，而 **_ftime32_s**僅代表 23:59:59 2038 年 1 月 18 日，UTC 日期。 1970 年 1 月 1 日午夜是所有這些函式的日期範圍下限。

**_Ftime_s**函數即相當於 **_ftime64_s**，和 **_timeb**包含 64 位元時間，除非 **_USE_32BIT_TIME_T**是定義，在此情況下舊的行為是作用中。**_ftime_s**使用 32 位元時間和 **_timeb**包含 32 位元時間。

**_ftime_s**會驗證其參數。 如果傳遞 null 做為指標*timeptr*，函式叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，函式會將**errno**至**EINVAL**。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**_ftime_s**|\<sys/types.h> 和 \<sys/timeb.h>|
|**_ftime32_s**|\<sys/types.h> 和 \<sys/timeb.h>|
|**_ftime64_s**|\<sys/types.h> 和 \<sys/timeb.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
