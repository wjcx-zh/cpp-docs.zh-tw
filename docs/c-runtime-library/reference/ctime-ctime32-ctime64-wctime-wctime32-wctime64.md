---
title: "ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ctime64
- _wctime32
- ctime
- _wctime64
- _ctime32
- _wctime
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
- _wctime64
- _ctime32
- _tctime
- _wctime
- _wctime32
- _tctime64
- _ctime64
- ctime
dev_langs:
- C++
helpviewer_keywords:
- tctime64 function
- _ctime32 function
- ctime32 function
- _wctime function
- wctime64 function
- _tctime64 function
- _tctime32 function
- _ctime64 function
- _wctime64 function
- ctime function
- wctime32 function
- ctime64 function
- _wctime32 function
- _tctime function
- tctime32 function
- tctime function
- wctime function
- time, converting
ms.assetid: 2423de37-a35c-4f0a-a378-3116bc120a9d
caps.latest.revision: 25
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: f3d756cec6d9482cfabcbc2a336cbf5d6381a97a
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="ctime-ctime32-ctime64-wctime-wctime32-wctime64"></a>ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64
將時間值轉換為字串並針對當地時區設定調整。 這些函式已有更安全的版本可用，請參閱 [ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
char *ctime(   
   const time_t *timer   
);  
char *_ctime32(   
   const __time32_t *timer )  
;  
char *_ctime64(   
   const __time64_t *timer )  
;  
wchar_t *_wctime(   
   const time_t *timer   
);  
wchar_t *_wctime32(   
   const __time32_t *timer  
);  
wchar_t *_wctime64(   
   const __time64_t *timer   
);  
```  
  
#### <a name="parameters"></a>參數  
 `timer`  
 預存時間的指標。  
  
## <a name="return-value"></a>傳回值  
 字元字串結果的指標。 如果是下列情況，則會傳回 `NULL`：  
  
-   `time` 代表 1970 年 1 月 1 日午夜 (UTC) 以前的日期。  
  
-   如果您使用 `_ctime32` 或 `_wctime32`，`time` 代表 2038 年 1 月 18 日 23:59:59 (UTC) 以後的日期。  
  
-   如果您使用 `_ctime64` 或 `_wctime64`，`time` 代表 3000 年 12 月 31 日 23:59:59 (UTC) 以後的日期。  
  
 `ctime` 是評估為 `_ctime64` 的內嵌函式，而 `time_t` 相當於 `__time64_t`。 如果您要強制編譯器將 `time_t` 解譯為舊的 32 位元 `time_t`，您可以定義 `_USE_32BIT_TIME_T`。 如此一來，將導致 `ctime` 評估 `_ctime32`。 建議您不要這樣做，原因是您的應用程式可能會在 2038 年 1 月 18 日後失敗，且在 64 位元平台上不允許這種定義。  
  
## <a name="remarks"></a>備註  
 `ctime` 函式會將儲存為 [time_t](../../c-runtime-library/standard-types.md) 值的時間值轉換為字元字串。 `timer` 值通常是透過對 [time](../../c-runtime-library/reference/time-time32-time64.md) 呼叫來取得，這會傳回自國際標準時間 (UTC) 1970 年 1 月 1 日午夜 (00:00:00) 起所經過的秒數。 傳回值字串剛好包含 26 個字元，且具有以下格式：  
  
```  
Wed Jan 02 02:03:55 1980\n\0  
```  
  
 使用 24 小時制。 所有欄位都具有固定寬度。 新行字元 ('\n') 和 null 字元 ('\0') 佔用字串的最後兩個位置。  
  
 已轉換的字元字串也會根據當地時區設定調整。 如需設定當地時間的資訊，請參閱 `time`、[_ftime](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) 和 [localtime](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)；如需定義時區環境及全域變數的詳細資訊，請參閱 [_tzset](../../c-runtime-library/reference/tzset.md) 函式。  
  
 呼叫 `ctime` 可修改 `gmtime` 和 `localtime` 函式所使用之單一靜態配置的緩衝區。 每呼叫其中一個此等常式會導致先前呼叫結果的終結。 `ctime` 會與 `asctime` 函式共用靜態緩衝區。 因此，呼叫 `ctime` 會終結任何先前對 `asctime`、`localtime` 或 `gmtime` 的呼叫結果。  
  
 `_wctime` 和 `_wctime64` 是寬字元版本的 `ctime` 和 `_ctime64`，並會傳回寬字元字串的指標。 否則，`_ctime64`、`_wctime` 和 `_wctime64` 的行為與 `ctime` 相同。  
  
 這些函式會驗證它們的參數。 如果 `timer` 是 null 指標，或如果計時器值為負數，則這些函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回 `NULL`，並將 `errno` 設定為 `EINVAL`。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tctime`|`ctime`|`ctime`|`_wctime`|  
|`_tctime32`|`_ctime32`|`_ctime32`|`_wctime32`|  
|`_tctime64`|`_ctime64`|`_ctime64`|`_wctime64`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`ctime`|\<time.h>|  
|`_ctime32`|\<time.h>|  
|`_ctime64`|\<time.h>|  
|`_wctime`|\<time.h> 或 \<wchar.h>|  
|`_wctime32`|\<time.h> 或 \<wchar.h>|  
|`_wctime64`|\<time.h> 或 \<wchar.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_ctime64.c  
// compile with: /W3  
/* This program gets the current  
 * time in _time64_t form, then uses ctime to  
 * display the time in string form.  
 */  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   __time64_t ltime;  
  
   _time64( &ltime );  
   printf( "The time is %s\n", _ctime64( &ltime ) ); // C4996  
   // Note: _ctime64 is deprecated; consider using _ctime64_s  
}  
```  
  
```Output  
The time is Wed Feb 13 16:04:43 2002  
```  
  
## <a name="see-also"></a>另請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)
