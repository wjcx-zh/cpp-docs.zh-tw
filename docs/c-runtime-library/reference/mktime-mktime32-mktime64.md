---
title: "mktime、_mktime32、_mktime64 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mktime32
- mktime
- _mktime64
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
- mktime
- _mktime64
dev_langs: C++
helpviewer_keywords:
- _mktime32 function
- mktime function
- time functions
- mktime64 function
- converting times
- mktime32 function
- _mktime64 function
- time, converting
ms.assetid: 284ed5d4-7064-48a2-bd50-15effdae32cf
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 33ab39945526ac2f53eab653ec374856953fc27e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mktime-mktime32-mktime64"></a>mktime、_mktime32、_mktime64
將當地時間轉換成月曆值。  
  
## <a name="syntax"></a>語法  
  
```  
time_t mktime(  
   struct tm *timeptr   
);  
__time32_t _mktime32(  
   struct tm *timeptr   
);  
__time64_t _mktime64(  
   struct tm *timeptr   
);  
```  
  
#### <a name="parameters"></a>參數  
 *timeptr*  
 時間結構的指標，請參閱 [asctime](../../c-runtime-library/reference/asctime-wasctime.md)。  
  
## <a name="return-value"></a>傳回值  
 `_mktime32` 會傳回指定的月曆時間，並編碼為 [time_t](../../c-runtime-library/standard-types.md) 類型的值。 如果*timeptr*參考 1970 年 1 月 1 日的午夜之前的日期或如果無法表示月曆時間，`_mktime32`傳回-1 轉換為類型`time_t`。 當使用`_mktime32`如果*timeptr*參考的日期之後 23:59:59 2038 年 1 月 18 日，Coordinated Universal Time (UTC)，它會傳回-1 轉換為類型`time_t`。  
  
 `_mktime64`會傳回-1 轉換為類型`__time64_t`如果*timeptr*參考 23:59:59，3000 年 12 月 31 日 UTC 之後的日期。  
  
## <a name="remarks"></a>備註  
 `mktime`、`_mktime32` 和 `_mktime64` 函式會將 *timeptr* 所指向的指定時間結構 (可能不完整)，轉換為具有標準化值的完整定義結構，然後將該結構轉換為 `time_t` 月曆時間值。 轉換後的時間和 [time](../../c-runtime-library/reference/time-time32-time64.md) 函式傳回的值具有相同的編碼。 會略過 *timeptr* 結構中 `tm_wday` 和 `tm_yday` 元件的原始值，且不會限制其他元件的原始值在其正確範圍中。  
  
 `mktime` 是相當於 `_mktime64` 的內嵌函式，但若有定義 `_USE_32BIT_TIME_T` 時，則是相當於 `_mktime32`。  
  
 調整為 UTC 之後，`_mktime32` 會處理從 1970 年 1 月 1 日午夜到 2038 年 1 月 18 日 23:59:59 (UTC) 之間的日期。 `_mktime64` 會處理從 1970 年 1 月 1 日到 3000 年 12 月 31 日 23:59:59 之間的日期。 即使您指定的日期是在範圍之內，此調整也可能會使這些函式傳回 -1 (轉換類型為 `time_t`、`__time32_t` 或 `__time64_t`)。 例如，您在開羅 (埃及)，此地區比 UTC 快兩小時，因此會先將 *timeptr* 中您指定的日期減去兩小時；而這麼做可能會使您的日期落在範圍之外。  
  
 可能會使用這些函式進行驗證及填寫 tm 結構。 若成功，這些函式會將 `tm_wday` 和 `tm_yday` 的值設定為適當的值，並設定其他元件，以表示指定的月曆時間，但同時也會強迫這些值在正確範圍內。 除非已經確認 `tm_mday` 和 `tm_mon`，否則不會設定 `tm_year` 的最終值。 當指定 `tm` 結構時間時，請將 `tm_isdst` 欄位設定為：  
  
-   零 (0)，以指出標準時間已生效。  
  
-   大於 0 的值，以指出日光節約時間已生效。  
  
-   小於 0 的值，使 C 執行階段程式庫程式碼計算標準時間或日光節約時間是否生效。  
  
 C 執行階段程式庫會從 [TZ](../../c-runtime-library/reference/tzset.md) 環境變數判斷日光節約時間行為。 若無設定 `TZ`，會使用 Win32 API 呼叫 [GetTimeZoneInformation](http://msdn.microsoft.com/library/windows/desktop/ms724421.aspx)，從作業系統取得日光節約時間資訊。 若此作業失敗，程式庫會在實作日光節約時間的計算時，假定使用美國的規則。 `tm_isdst` 是必要的欄位。 若無設定，該值會是未定義，而且這些函式的傳回值會無法預期。 若 *timeptr* 指向之前呼叫 `asctime`、`gmtime` 或 `localtime` (或是這些函式的變體) 所傳回的 `tm` 結構，則 `tm_isdst` 欄位包含正確的值。  
  
 請注意，`gmtime` 及 `localtime` (和 `_gmtime32`、`_gmtime64`、`_localtime32` 和 `_localtime64`) 會針對轉換，為每個執行緒使用單一緩衝區。 若您將此緩衝區提供給 `mktime`、`_mktime32` 或 `_mktime64`，則會終結之前的內容。  
  
 這些函式會驗證它們的參數。 如果 *timeptr* 為 null 指標，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，函式會傳回 -1，並將 `errno` 設為 `EINVAL`。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`mktime`|\<time.h>|  
|`_mktime32`|\<time.h>|  
|`_mktime64`|\<time.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_mktime.c  
/* The example takes a number of days  
 * as input and returns the time, the current  
 * date, and the specified number of days.  
 */  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   struct tm  when;  
   __time64_t now, result;  
   int        days;  
   char       buff[80];  
  
   time( &now );  
   _localtime64_s( &when, &now );  
   asctime_s( buff, sizeof(buff), &when );  
   printf( "Current time is %s\n", buff );  
   days = 20;  
   when.tm_mday = when.tm_mday + days;  
   if( (result = mktime( &when )) != (time_t)-1 ) {  
      asctime_s( buff, sizeof(buff), &when );  
      printf( "In %d days the time will be %s\n", days, buff );  
   } else  
      perror( "mktime failed" );  
}  
```  
  
## <a name="sample-output"></a>範例輸出  
  
```  
Current time is Fri Apr 25 13:34:07 2003  
  
In 20 days the time will be Thu May 15 13:34:07 2003  
```  
  
## <a name="see-also"></a>請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [_mkgmtime、_mkgmtime32、_mkgmtime64](../../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)