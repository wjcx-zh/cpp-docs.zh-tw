---
title: "_mkgmtime、_mkgmtime32、_mkgmtime64 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
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
- _mkgmtime64
- mkgmtime32
- _mkgmtime32
- mkgmtime
- mkgmtime64
- _mkgmtime
dev_langs:
- C++
helpviewer_keywords:
- mkgmtime32 function
- time functions
- mkgmtime function
- _mkgmtime function
- converting times
- mkgmtime64 function
- _mkgmtime64 function
- _mkgmtime32 function
- time, converting
ms.assetid: b4ca2b67-e198-4f43-b3e2-e8ad6bd01867
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 7f73bffc2971b535f393cef7e0e2f957b01eee42
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="mkgmtime-mkgmtime32-mkgmtime64"></a>_mkgmtime、_mkgmtime32、_mkgmtime64
將以 `tm``struct` 表示的 UTC 時間，轉換成以 `time_t` 類型表示的 UTC 時間。  
  
## <a name="syntax"></a>語法  
  
```  
  
      time_t _mkgmtime(  
   struct tm* timeptr  
);  
__time32_t _mkgmtime32(  
   struct tm* timeptr  
);  
__time64_t _mkgmtime64(  
   struct tm* timeptr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `timeptr`  
 要轉換之 UTC 時間的指標，以 `struct``tm` 表示。  
  
## <a name="return-value"></a>傳回值  
 `__time32_t` 或 `__time64_t` 類型的數量，代表自國際標準時間 (UTC) 1970 年 1 月 1 日午夜以來所經過的秒數。 如果日期超出範圍 （請參閱 < 備註 > 一節） 或輸入無法解譯為有效的時間，傳回的值為-1。  
  
## <a name="remarks"></a>備註  
 `_mkgmtime32` 和 `_mkgmtime64` 函式會將 UTC 時間，轉換成代表 UTC 時間的 `__time32_t` 或 `__time64_t` 類型。 若要將當地時間轉換成 UTC 時間，請改用 `mktime`、`_mktime32` 和 `_mktime64`。  
  
 `_mkgmtime` 是評估為 `_mkgmtime64` 的內嵌函式，而 `time_t` 相當於 `__time64_t`。 如果您要強制編譯器將 `time_t` 解譯為舊的 32 位元 `time_t`，您可以定義 `_USE_32BIT_TIME_T`。 建議您不要這樣做，原因是您的應用程式可能會在 2038 年 1 月 18 日 (32 位元 `time_t` 的最大範圍) 後失敗，而且完全不允許在 64 位元平台上使用。  
  
 傳入的時間結構會如下變更，就像是使用 `_mktime` 函式來變更一樣︰`tm_wday` 和 `tm_yday` 欄位會根據 `tm_mday` 和 `tm_year` 的值設定為新值。 當指定 `tm` 結構時間時，請將 `tm_isdst` 欄位設定為：  
  
-   零 (0)，以指出標準時間已生效。  
  
-   大於 0 的值，以指出日光節約時間已生效。  
  
-   小於 0 的值，使 C 執行階段程式庫程式碼計算標準時間或日光節約時間是否生效。  
  
 C 執行階段程式庫使用 TZ 環境變數來判斷正確的日光節約時間。 如果未設定 TZ，則會查詢作業系統以取得正確的地區日光節約時間行為。 `tm_isdst` 是必要的欄位。 若無設定，該值會是未定義，而且 `mktime` 的傳回值會無法預期。  
  
 `_mkgmtime32` 函式的範圍是從 1970 年 1 月 1 日午夜 (UTC) 到 2038 年 1 月 18 日 23:59:59 (UTC)。 `_mkgmtime64` 的範圍是從 1970 年 1 月 1 日午夜 (UTC) 到 3000 年 12 月 31 日 23:59:59 (UTC)。 傳回值-1 會產生超出範圍的日期。 `_mkgmtime` 的範圍取決於是否定義 `_USE_32BIT_TIME_T`。 如果未定義 (預設)，則會是 `_mkgmtime64` 的範圍；否則範圍會限制在 `_mkgmtime32` 的 32 位元範圍。  
  
 請注意，`gmtime` 和 `localtime` 使用單一靜態配置的緩衝區來進行轉換。 若您將此緩衝區提供給 `mkgmtime`，則會終結之前的內容。  
  
## <a name="example"></a>範例  
  
```  
// crt_mkgmtime.c  
#include <stdio.h>  
#include <time.h>  
  
int main()  
{  
    struct tm t1, t2;  
    time_t now, mytime, gmtime;  
    char buff[30];  
  
    time( & now );  
  
    _localtime64_s( &t1, &now );  
    _gmtime64_s( &t2, &now );  
  
    mytime = mktime(&t1);  
    gmtime = _mkgmtime(&t2);  
  
    printf("Seconds since midnight, January 1, 1970\n");  
    printf("My time: %I64d\nGM time (UTC): %I64d\n\n", mytime, gmtime);  
  
    /* Use asctime_s to display these times. */  
  
    _localtime64_s( &t1, &mytime );  
    asctime_s( buff, sizeof(buff), &t1 );  
    printf( "Local Time: %s\n", buff );  
  
    _gmtime64_s( &t2, &gmtime );  
    asctime_s( buff, sizeof(buff), &t2 );  
    printf( "Greenwich Mean Time: %s\n", buff );  
  
}  
```  
  
## <a name="sample-output"></a>範例輸出  
  
```  
Seconds since midnight, January 1, 1970  
My time: 1171588492  
GM time (UTC): 1171588492  
  
Local Time: Thu Feb 15 17:14:52 2007  
  
Greenwich Mean Time: Fri Feb 16 01:14:52 2007  
```  
  
 下列範例示範如何以星期幾和年份日期的計算值填滿不完整的結構。  
  
```  
// crt_mkgmtime2.c  
#include <stdio.h>  
#include <time.h>  
#include <memory.h>  
  
int main()  
{  
    struct tm t1, t2;  
    time_t gmtime;  
    char buff[30];  
  
    memset(&t1, 0, sizeof(struct tm));  
    memset(&t2, 0, sizeof(struct tm));  
  
    t1.tm_mon = 1;  
    t1.tm_isdst = 0;  
    t1.tm_year = 103;  
    t1.tm_mday = 12;  
  
    // The day of the week and year will be incorrect in the output here.  
    asctime_s( buff, sizeof(buff), &t1);  
    printf("Before calling _mkgmtime, t1 = %s t.tm_yday = %d\n",  
            buff, t1.tm_yday );  
  
    gmtime = _mkgmtime(&t1);  
  
    // The correct day of the week and year were determined.  
    asctime_s( buff, sizeof(buff), &t1);  
    printf("After calling _mkgmtime, t1 = %s t.tm_yday = %d\n",  
            buff, t1.tm_yday );  
  
}  
```  
  
## <a name="output"></a>輸出  
  
```  
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003  
 t.tm_yday = 0  
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003  
 t.tm_yday = 42  
```  
  
## <a name="see-also"></a>另請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [gmtime_s、_gmtime32_s、_gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s、_localtime32_s、_localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [mktime、_mktime32、_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)
