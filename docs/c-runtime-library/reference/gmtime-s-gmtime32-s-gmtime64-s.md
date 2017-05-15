---
title: "gmtime_s、_gmtime32_s、_gmtime64_s | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _gmtime32_s
- gmtime_s
- _gmtime64_s
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
- _gmtime_s
- gmtime64_s
- gmtime32_s
- _gmtime64_s
- gmtime_s
- _gmtime32_s
dev_langs:
- C++
helpviewer_keywords:
- gmtime_s function
- gmtime32_s function
- time functions
- gmtime64_s function
- _gmtime64_s function
- time structure conversion
- _gmtime_s function
- _gmtime32_s function
ms.assetid: 261c7df0-2b0c-44ba-ba61-cb83efaec60f
caps.latest.revision: 29
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
ms.openlocfilehash: e130b125651c29a4ba2607b47b02b95c81468869
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="gmtimes-gmtime32s-gmtime64s"></a>gmtime_s、_gmtime32_s、_gmtime64_s
將時間值轉換成結構。 這些是具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) 版本。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t gmtime_s(  
   struct tm* _tm,  
   const __time_t* time  
);  
errno_t _gmtime32_s(  
   struct tm* _tm,  
   const __time32_t* time  
);  
errno_t _gmtime64_s(  
   struct tm* _tm,  
   const __time64_t* time   
);  
```  
  
#### <a name="parameters"></a>參數  
 `_tm`  
 `tm` 結構的指標。 傳回結構的欄位以 UTC 來保存 `timer` 引數的評估值，而非當地時間。  
  
 `time`  
 預存時間的指標。 時間以國際標準時間 1970 年 1 月 1 日 (UTC) 午夜 (00: 00:00) 以來經過的秒代表。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則為零。 如果失敗，傳回的值會是錯誤碼。 錯誤碼於 Errno.h 中定義；如需這些錯誤的清單，請參閱 [errno](../../c-runtime-library/errno-constants.md)。  
  
### <a name="error-conditions"></a>錯誤狀況  
  
|`_tm`|`time`|返回|`_tm` 中的值|  
|-----------|------------|------------|--------------------|  
|`NULL`|任何|`EINVAL`|未修改。|  
|非 `NULL` (指向有效的記憶體)|`NULL`|`EINVAL`|所有的欄位設定為 -1。|  
|非 `NULL`|< 0|`EINVAL`|所有的欄位設定為 -1。|  
  
 在前兩個錯誤狀況的情況下，會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 `EINVAL`。  
  
## <a name="remarks"></a>備註  
 `_gmtime32_s` 函式會細分 `time` 值，並將它儲存在 `tm` 類型的結構中，如 Time.h 中所定義。 結構的位址會傳入 `_tm`。 `time` 的值通常取自對 `time` 函式的呼叫。  
  
> [!NOTE]
>  目標環境應該嘗試判斷日光節約時間是否生效。 C 執行階段程式庫會假定使用美國的規則，以實作日光節約時間的計算。  
  
 每個結構欄位是 `int` 類型，如下表所示。  
  
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
  
 使用 `__time64_t` 結構的 `_gmtime64_s`，允許表示至 3000 年 12 月 31 日 23:59:59 UTC 為止的日期，而 `gmtime32_s` 只能表示至 2038 年 1 月 18 日23:59:59 UTC 的日期。 1970 年 1 月 1 日午夜是所有這兩個函式的日期範圍下限。  
  
 `gmtime_s` 是內嵌函式，其評估 `_gmtime64_s` 和 `time_t` 是否相當於 `__time64_t`。 如果您要強制編譯器將 `time_t` 解譯為舊的 32 位元`time_t`，您可以定義 `_USE_32BIT_TIME_T`。 如此一來，將導致 `gmtime_s` 內嵌至`_gmtime32_s`。 建議您不要這樣做，原因是您的應用程式可能會在 2038 年 1 月 18 日後失敗，且在 64 位元平台上不允許這種定義。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`gmtime_s`|\<time.h>|  
|`_gmtime32_s`|\<time.h>|  
|`_gmtime64_s`|\<time.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_gmtime64_s.c  
// This program uses _gmtime64_s to convert a 64-bit  
// integer representation of coordinated universal time  
// to a structure named newtime, then uses asctime_s to  
// convert this structure to an output string.  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   struct tm newtime;  
   __int64 ltime;  
   char buf[26];  
   errno_t err;  
  
   _time64( &ltime );  
  
   // Obtain coordinated universal time:   
   err = _gmtime64_s( &newtime, &ltime );  
   if (err)  
   {  
      printf("Invalid Argument to _gmtime64_s.");  
   }  
  
   // Convert to an ASCII representation   
   err = asctime_s(buf, 26, &newtime);  
   if (err)  
   {  
      printf("Invalid Argument to asctime_s.");  
   }  
  
   printf( "Coordinated universal time is %s\n",   
           buf );  
}  
```  
  
```Output  
Coordinated universal time is Fri Apr 25 20:12:33 2003  
```  
  
## <a name="see-also"></a>另請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime_s、_localtime32_s、_localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [_mkgmtime、_mkgmtime32、_mkgmtime64](../../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)   
 [mktime、_mktime32、_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)
