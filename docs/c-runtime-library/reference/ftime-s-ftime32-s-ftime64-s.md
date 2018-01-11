---
title: "_ftime_s、_ftime32_s、_ftime64_s | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: eb90c8f9ed18355821e3a067b0f2b9b92562b08c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ftimes-ftime32s-ftime64s"></a>_ftime_s、_ftime32_s、_ftime64_s
取得目前時間。 這些是具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) 版本。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t _ftime_s(   
   struct _timeb *timeptr   
);  
errno_t _ftime32_s(   
   struct __timeb32 *timeptr   
);  
errno_t _ftime64_s(   
   struct __timeb64 *timeptr   
);  
```  
  
#### <a name="parameters"></a>參數  
 `timeptr`  
 指標`_timeb`， `__timeb32`，或`__timeb64`結構。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則為零，如果失敗，則為錯誤碼。 如果 `timeptr` 為 `NULL`，則傳回值是 `EINVAL`。  
  
## <a name="remarks"></a>備註  
 `_ftime_s`函式取得目前的當地時間，並將它儲存在結構中所指`timeptr`。 `_timeb`， `__timeb32`，和`__timeb64`SYS\Timeb.h 中所定義的結構。 它們包含下表中所列出的四個欄位。  
  
 `dstflag`  
 若日光節約時間目前於本地時區已生效，則為非零。 (如需如何判斷日光節約時間的說明，請參閱 [_tzset](../../c-runtime-library/reference/tzset.md)。)  
  
 `millitm`  
 秒數的分數，以毫秒為單位。  
  
 `time`  
 自國際標準時間 (UTC) 1970 年 1 月 1 日午夜 (00:00:00) 以來的時間，以秒為單位。  
  
 `timezone`  
 UTC 和當地時間之間的時差，向西推進，以分鐘為單位。 `timezone` 的值由全域變數 `_timezone` 的值設定 (請參閱 `_tzset`)。  
  
 使用 `__timeb64` 結構的 `_ftime64_s`，允許表示至 3000 年 12 月 31 日 23:59:59 UTC 為止的日期，而 `_ftime32_s` 只能表示至 2038 年 1 月 18 日23:59:59 UTC 的日期。 1970 年 1 月 1 日午夜是所有這些函式的日期範圍下限。  
  
 `_ftime_s` 相當於 `_ftime64_s`，且 `_timeb` 包含 64 位元時間。 上述情況只有在定義 `_USE_32BIT_TIME_T` 時才成立，在此情況下，會採用舊版行為，也就是 `_ftime_s` 使用 32 位元時間，且 `_timeb` 包含 32 位元時間。  
  
 `_ftime_s` 會驗證其參數。 如果以 `timeptr` 傳遞 Null 指標，則此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則函式會將 `errno` 設為 `EINVAL`。  
  
## <a name="requirements"></a>需求  
  
|功能|必要的標頭|  
|--------------|---------------------|  
|`_ftime_s`|\<sys/types.h> 和 \<sys/timeb.h>|  
|`_ftime32_s`|\<sys/types.h> 和 \<sys/timeb.h>|  
|`_ftime64_s`|\<sys/types.h> 和 \<sys/timeb.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
  
```  
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
  
## <a name="see-also"></a>請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)