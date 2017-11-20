---
title: "asctime_s、_wasctime_s | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wasctime_s
- asctime_s
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
- asctime_s
- _wasctime_s
- _tasctime_s
dev_langs: C++
helpviewer_keywords:
- tasctime_s function
- _tasctime_s function
- time structure conversion
- wasctime_s function
- time, converting
- _wasctime_s function
- asctime_s function
ms.assetid: 17ad9b2b-a459-465d-976a-42822897688a
caps.latest.revision: "29"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4b72b82e1b8c7ae2d036d35b00e8a49b7516d64b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="asctimes-wasctimes"></a>asctime_s、_wasctime_s
將 `tm` 時間結構轉換成字元字串。 這是如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之增強安全性的 [asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md) 版本。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t asctime_s(   
   char* buffer,  
   size_t numberOfElements,  
   const struct tm *_tm   
);  
errno_t _wasctime_s(   
   wchar_t* buffer,  
   size_t numberOfElements  
   const struct tm *_tm   
);  
template <size_t size>  
errno_t asctime_s(   
   char (&buffer)[size],  
   const struct tm *_tm   
); // C++ only  
template <size_t size>  
errno_t _wasctime_s(   
   wchar_t (&buffer)[size],  
   const struct tm *_tm   
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 `buffer`  
 [out] 儲存字元字串結果的緩衝區指標。 此函式假設有效的記憶體位置指標，其大小由 `numberOfElements` 指定。  
  
 `numberOfElements`  
 [in] 儲存結果所使用的緩衝區大小。  
  
 `_tm`  
 [in] 時間/日期結構。 此函式會假設有效 `struct tm` 物件的指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則為零。 如果失敗，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，傳回值為錯誤碼。 錯誤碼於 ERRNO.H 中定義。 如需詳細資訊，請參閱 [errno 常數](../../c-runtime-library/errno-constants.md)。 下表顯示每個錯誤條件所傳回的實際錯誤碼。  
  
### <a name="error-conditions"></a>錯誤狀況  
  
|`buffer`|`numberOfElements`|`tm`|返回|`buffer` 中的值|  
|--------------|------------------------|----------|------------|-----------------------|  
|`NULL`|任何|任何|`EINVAL`|未修改|  
|不是 `NULL` (指向有效的記憶體)|0|任何|`EINVAL`|未修改|  
|不是 `NULL`|0< 大小 < 26|任何|`EINVAL`|空字串|  
|不是 `NULL`|>= 26|`NULL`|`EINVAL`|空字串|  
|不是 `NULL`|>= 26|無效的時間結構或超出時間元件值的範圍|`EINVAL`|空字串|  
  
> [!NOTE]
>  `wasctime_s` 的錯誤條件類似以文字量測大小限制之例外狀況的 `asctime_s`。  
  
## <a name="remarks"></a>備註  
 `asctime` 函式會將儲存為結構的時間轉換為字元字串。 `_tm` 值通常取自於 `gmtime` 或 `localtime` 呼叫。 這兩個函式都可用來填入 `tm` 結構，如 TIME.H 所定義。  
  
|timeptr 成員|值|  
|--------------------|-----------|  
|`tm_hour`|午夜 (0-23) 的小時|  
|`tm_isdst`|若日光節約時間已生效則為正值；如果日光節約時間沒有作用則為 0。如果日光節約時間的狀態是未知，則為負值。 C 執行階段程式庫會在實作日光節約時間 (DST) 的計算時，使用美國的規則。|  
|`tm_mday`|月份 (1-31) 天數|  
|`tm_min`|小時 (0-59) 之後的分鐘|  
|`tm_mon`|月 (0-11。年 1 月 = 0）|  
|`tm_sec`|分鐘 (0-59) 之後的秒數|  
|`tm_wday`|(0-6; 週間日星期日 = 0）|  
|`tm_yday`|年 (0 365; 中的日年 1 月 1 = 0)|  
|`tm_year`|年份 (目前年份減去 1900 年)|  
  
 已轉換的字元字串也會根據本機時區設定調整。 如需設定本機時間的資訊，請參閱 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)、[_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) 及 [localtime_s、_localtime32_s、_localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md) 函式；如需定義時區環境及全域變數的資訊，請參閱 [_tzset](../../c-runtime-library/reference/tzset.md) 函式。  
  
 `asctime_s` 所產生的字串結果剛好包含 26 個字元，且具有以下格式 `Wed Jan 02 02:03:55 1980\n\0`。 使用 24 小時制。 所有欄位都具有固定寬度。 新行字元和 Null 字元佔用字串的最後兩個位置。 當作第二個參數傳入的值至少應有這麼大。 如果更小，就會傳回錯誤碼 `EINVAL`。  
  
 `_wasctime_s` 是 `asctime_s` 的寬字元版本。 否則，`_wasctime_s` 和 `asctime_s` 的行為即會相同。  
  
### <a name="generic-text-routine-mapping"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tasctime_s`|`asctime_s`|`asctime_s`|`_wasctime_s`|  
  
 C++ 中，使用這些函式已為範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`asctime_s`|\<time.h>|  
|`_wasctime_s`|\<time.h> 或 \<wchar.h>|  
  
## <a name="security"></a>安全性  
 如果緩衝區指標不是 `NULL` 且指標不指向有效的緩衝區，則函式會覆寫該位置的任何內容。 這也會導致存取違規。  
  
 如果傳入的大小引數大於緩衝區的實際大小，就會發生[緩衝區滿溢](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
## <a name="example"></a>範例  
 此程式會將系統時間放在長整數 `aclock` 中，將其轉譯成結構 `newtime`，然後使用 `asctime_s` 函式將它轉換成字串格式以供輸出。  
  
```  
// crt_asctime_s.c  
#include <time.h>  
#include <stdio.h>  
  
struct tm newtime;  
__time32_t aclock;  
  
int main( void )  
{  
   char buffer[32];  
   errno_t errNum;  
   _time32( &aclock );   // Get time in seconds.  
   _localtime32_s( &newtime, &aclock );   // Convert time to struct tm form.  
  
   // Print local time as a string.  
  
   errNum = asctime_s(buffer, 32, &newtime);  
   if (errNum)  
   {  
       printf("Error code: %d", (int)errNum);  
       return 1;  
   }  
   printf( "Current date and time: %s", buffer );  
   return 0;  
}  
```  
  
```Output  
Current date and time: Wed May 14 15:30:17 2003  
```  
  
## <a name="see-also"></a>另請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime_s、_gmtime32_s、_gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s、_localtime32_s、_localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)