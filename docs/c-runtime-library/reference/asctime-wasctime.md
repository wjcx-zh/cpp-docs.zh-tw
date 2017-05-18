---
title: "asctime、_wasctime | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wasctime
- asctime
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
- _tasctime
- asctime
- _wasctime
dev_langs:
- C++
helpviewer_keywords:
- asctime function
- tasctime function
- wasctime function
- _tasctime function
- _wasctime function
- time structure conversion
- time, converting
ms.assetid: 974f1727-10ff-4ed4-8cac-2eb2d681f576
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.openlocfilehash: 91f0ffd5b02f9e8bc34604683c6274ec0f2c28b3
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="asctime-wasctime"></a>asctime、_wasctime
將 `tm` 時間結構轉換成字元字串。 這些函式有更安全的版本可用，請參閱 [asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
char *asctime(   
   const struct tm *timeptr   
);  
wchar_t *_wasctime(   
   const struct tm *timeptr   
);  
```  
  
#### <a name="parameters"></a>參數  
 `timeptr`  
 時間/日期結構。  
  
## <a name="return-value"></a>傳回值  
 `asctime` 會傳回字元字串結果的指標，`_wasctime` 會傳回寬字元字串結果的指標。 沒有錯誤傳回值。  
  
## <a name="remarks"></a>備註  
 這些函式有更安全的版本可用，請參閱 [asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)。  
  
 `asctime` 函式會將儲存為結構的時間轉換為字元字串。 `timeptr` 值通常取自於 `gmtime` 或 `localtime` 呼叫，這兩者都會傳回 TIME.H 中定義的 `tm` 結構指標。  
  
|timeptr 成員|值|  
|--------------------|-----------|  
|`tm_hour`|小時午夜 (0-23)|  
|`tm_isdst`|若日光節約時間已生效則為正值；如果日光節約時間沒有作用則為 0。如果日光節約時間的狀態是未知，則為負值。 C 執行階段程式庫會在實作日光節約時間 (DST) 的計算時，使用美國的規則。|  
|`tm_mday`|月份 (1-31) 天數|  
|`tm_min`|小時 (0-59) 之後的分鐘|  
|`tm_mon`|月 (0-11。年 1 月 = 0）|  
|`tm_sec`|分鐘 (0-59) 之後的秒數|  
|`tm_wday`|(0-6; 週間日星期日 = 0）|  
|`tm_yday`|年 (0 365; 中的日年 1 月 1 = 0)|  
|`tm_year`|年份 (目前年份減去 1900 年)|  
  
 已轉換的字元字串也會根據本機時區設定調整。 如需設定本機時間的資訊，請參閱 [time](../../c-runtime-library/reference/time-time32-time64.md)、[_ftime](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) 和 [localtime](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) 函式；如需定義時區環境及全域變數的資訊，請參閱 [_tzset](../../c-runtime-library/reference/tzset.md) 函式。  
  
 `asctime` 所產生的字串結果剛好包含 26 個字元，且具有以下格式 `Wed Jan 02 02:03:55 1980\n\0`。 使用 24 小時制。 所有欄位都具有固定寬度。 新行字元和 Null 字元佔用字串的最後兩個位置。 `asctime` 使用單一的靜態配置緩衝區來容納傳回的字串。 每次呼叫此函式都會導致先前呼叫結果的終結。  
  
 `_wasctime` 是 `asctime` 的寬字元版本。 否則，`_wasctime` 和 `asctime` 的行為即會相同。  
  
 這些函式會驗證它們的參數。 如果 `timeptr` 是 Null 指標，或如果它包含超出範圍的值，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，函式會傳回 `NULL`，並將 `errno` 設為 `EINVAL`。  
  
### <a name="generic-text-routine-mapping"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tasctime`|`asctime`|`asctime`|`_wasctime`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`asctime`|\<time.h>|  
|`_wasctime`|\<time.h> 或 \<wchar.h>|  
  
## <a name="example"></a>範例  
 此程式會將系統時間放在長整數 `aclock` 中，將其轉譯成結構 `newtime`，然後使用 `asctime` 函式將它轉換成字串格式以供輸出。  
  
```  
// crt_asctime.c  
// compile with: /W3  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
    struct tm   *newTime;  
    time_t      szClock;  
  
    // Get time in seconds  
    time( &szClock );  
  
    // Convert time to struct tm form   
    newTime = localtime( &szClock );  
  
    // Print local time as a string.  
    printf_s( "Current date and time: %s", asctime( newTime ) ); // C4996  
    // Note: asctime is deprecated; consider using asctime_s instead  
}  
```  
  
```Output  
Current date and time: Sun Feb 03 11:38:58 2002  
```  
  
## <a name="see-also"></a>另請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)   
 [asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)
