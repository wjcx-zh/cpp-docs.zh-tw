---
title: "gmtime、_gmtime32、_gmtime64 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _gmtime32
- gmtime
- _gmtime64
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
- gmtime
- _gmtime32
- _gmtime64
dev_langs:
- C++
helpviewer_keywords:
- gmtime32 function
- _gmtime64 function
- gmtime function
- time functions
- _gmtime32 function
- gmtime64 function
- time structure conversion
ms.assetid: 315501f3-477e-475d-a414-ef100ee0db27
caps.latest.revision: 30
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: d6acd03622ffd309e394fc076c2922492ac2475b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="gmtime-gmtime32-gmtime64"></a>gmtime、_gmtime32、_gmtime64
將時間值轉換成結構。 這些函式有更安全的版本可供使用；請參閱 [gmtime_s、_gmtime32_s、_gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
struct tm *gmtime(   
   const time_t *timer   
);  
struct tm *_gmtime32(   
   const __time32_t *timer   
);  
struct tm *_gmtime64(   
   const __time64_t *timer   
);  
```  
  
#### <a name="parameters"></a>參數  
 `timer`  
 預存時間的指標。 時間以國際標準時間 1970 年 1 月 1 日 (UTC) 午夜 (00: 00:00) 以來經過的秒代表。  
  
## <a name="return-value"></a>傳回值  
 [tm](../../c-runtime-library/standard-types.md) 類型之結構的指標。 傳回結構的欄位以 UTC 來保存 `timer` 引數的評估值，而非當地時間。 每個結構欄位的類型是 `int`，如下所示︰  
  
 `tm_sec`  
 分鐘之後的秒數 (0-59)。  
  
 `tm_min`  
 小時之後的分鐘 (0-59)。  
  
 `tm_hour`  
 從午夜開始的小時 (0-23)。  
  
 `tm_mday`  
 日期的月份 (1-31)。  
  
 `tm_mon`  
 月 (0-11。年 1 月 = 0）。  
  
 `tm_year`  
 年份 (目前年份減去 1900)。  
  
 `tm_wday`  
 一週天數 (0-6;星期日 = 0）。  
  
 `tm_yday`  
 年中的日 (0-365;年 1 月 1 = 0)。  
  
 `tm_isdst`  
 `gmtime` 一律為 0。  
  
 32 位元和 64 位元版本的 `gmtime`、`mktime`、`mkgmtime`和`localtime` 進行轉換時每個執行緒都使用單一的 `tm` 結構。 每次呼叫這些函式的其中之一時，會終結任何先前呼叫的結果。 如果 `timer` 代表 1970 年 1 月 1 日午夜以前的日期，`gmtime` 會傳回 `NULL`。 不會傳回錯誤。  
  
 使用 `__time64_t` 結構的 `_gmtime64`，允許表示至 3000 年 12 月 31 日 23:59:59 UTC 為止的日期，而 `_gmtime32` 只能表示至 2038 年 1 月 18 日23:59:59 UTC 的日期。 1970 年 1 月 1 日午夜是這兩個函式的日期範圍下限。  
  
 `gmtime` 是內嵌函式，其評估為 `_gmtime64`，且除非 `_USE_32BIT_TIME_T` 已定義，否則 `time_t` 相當於 `__time64_t`。 如果您必須強制編譯器將 `time_t` 解譯為舊的 32 位元 `time_t`，您可以定義 `_USE_32BIT_TIME_T`，但是這樣做會導致`gmtime` 內嵌至 `_gmtime32`，且 `time_t` 被定義為 `__time32_t`。 我們建議您不要這麼做，因為 64 位元平台上不允許這種定義，而且在任何情況下，您的應用程式可能會在 2038 年 1 月 18 日之後失敗。  
  
 這些函式會驗證它們的參數。 如果 `timer` 是 Null 指標，或如果計時器值為負值，則這些函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，函式會傳回 `NULL`，並將 `errno` 設為 `EINVAL`。  
  
## <a name="remarks"></a>備註  
 `_gmtime32` 函式會細分`timer` 值，並將它儲存在 `tm` 類型的結構中，如 TIME.H 中所定義。 `timer` 的值通常取自對 `time` 函式的呼叫。  
  
> [!NOTE]
>  在大部分情況下，目標環境會嘗試判斷日光節約時間是否生效。 C 執行階段程式庫會假定使用美國的規則，以實作日光節約時間 (DST) 的計算。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`gmtime`|\<time.h>|  
|`_gmtime32`|\<time.h>|  
|`_gmtime64`|\<time.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```C  
// crt_gmtime.c  
// compile with: /W3  
// This program uses _gmtime64 to convert a long-  
// integer representation of coordinated universal time  
// to a structure named newtime, then uses asctime to  
// convert this structure to an output string.  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   struct tm *newtime;  
   __int64 ltime;  
   char buff[80];  
  
   _time64( &ltime );  
  
   // Obtain coordinated universal time:  
   newtime = _gmtime64( &ltime ); // C4996  
   // Note: _gmtime64 is deprecated; consider using _gmtime64_s  
   asctime_s( buff, sizeof(buff), newtime );  
   printf( "Coordinated universal time is %s\n", buff );  
}  
```  
  
```Output  
Coordinated universal time is Tue Feb 12 23:11:31 2002  
```  
  
## <a name="see-also"></a>另請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime_s、_gmtime32_s、_gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [_mkgmtime、_mkgmtime32、_mkgmtime64](../../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)   
 [mktime、_mktime32、_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)
