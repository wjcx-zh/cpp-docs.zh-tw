---
title: "ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _ctime64_s
- _wctime32_s
- ctime_s
- _wctime64_s
- _ctime32_s
- _wctime_s
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
- ctime64_s
- _ctime32_s
- _tctime32_s
- _ctime64_s
- _wctime_s
- _tctime_s
- _tctime64_s
- ctime_s
- ctime32_s
dev_langs:
- C++
helpviewer_keywords:
- _wctime32_s function
- ctime64_s function
- _tctime64_s function
- _wctime_s function
- tctime_s function
- _wctime64_s function
- ctime_s function
- ctime32_s function
- _ctime64_s function
- tctime64_s function
- wctime64_s function
- wctime_s function
- _tctime_s function
- tctime32_s function
- wctime32_s function
- time, converting
- _ctime32_s function
- _tctime32_s function
ms.assetid: 36ac419a-8000-4389-9fd8-d78b747a009b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 998046c0d59d12cd14d9091d9054312c5d1d48a2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="ctimes-ctime32s-ctime64s-wctimes-wctime32s-wctime64s"></a>ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s
將時間值轉換為字串並針對當地時區設定調整。 這些是具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [ctime、_ctime64、_wctime、_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) 版本。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t ctime_s(   
   char* buffer,  
   size_t numberOfElements,  
   const time_t *time   
);  
errno_t _ctime32_s(   
   char* buffer,  
   size_t numberOfElements,  
   const __time32_t *time   
);  
errno_t _ctime64_s(   
   char* buffer,  
   size_t numberOfElements,  
   const __time64_t *time )  
;  
errno_t _wctime_s(   
   wchar_t* buffer,  
   size_t numberOfElements,  
   const time_t *time   
);  
errno_t _wctime32_s(   
   wchar_t* buffer,  
   size_t numberOfElements,  
   const __time32_t *time   
);  
errno_t _wctime64_s(   
   wchar_t* buffer,  
   size_t numberOfElements,  
   const __time64_t *time   
);  
template <size_t size>  
errno_t _ctime32_s(   
   char (&buffer)[size],  
   const __time32_t *time   
); // C++ only  
template <size_t size>  
errno_t _ctime64_s(   
   char (&buffer)[size],  
   const __time64_t *time  
); // C++ only  
template <size_t size>  
errno_t _wctime32_s(   
   wchar_t (&buffer)[size],  
   const __time32_t *time   
); // C++ only  
template <size_t size>  
errno_t _wctime64_s(   
   wchar_t (&buffer)[size],  
   const __time64_t *time   
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 [輸出] `buffer`  
 必須足以容納 26 個字元。 字元字串結果時，指標或`NULL`如果：  
  
-   `time` 代表 1970 年 1 月 1 日午夜 (UTC) 以前的日期。  
  
-   如果您使用 `_ctime32_s` 或 `_wctime32_s`，`time` 代表 2038 年 1 月 18 日 23:59:59 (UTC) 以後的日期。  
  
-   如果您使用 `_ctime64_s` 或 `_wctime64_s`，`time` 代表 3000 年 12 月 31 日 23:59:59 (UTC) 以後的日期。  
  
-   如果您使用 `_ctime_s` 或 `_wctime_s`，這些函式是先前函式的包裝函式。 請參閱＜備註＞一節。  
  
 [輸入] `numberOfElements`  
 緩衝區的大小。  
  
 [輸入] `time`  
 預存時間的指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則為零。 如果由於參數無效而失敗，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則會傳回錯誤碼。 錯誤碼是在 ERRNO.H 中定義；如需這些錯誤的清單，請參閱 [errno](../../c-runtime-library/errno-constants.md)。 下表顯示每個錯誤條件所擲回的實際錯誤碼。  
  
## <a name="error-conditions"></a>錯誤狀況  
  
|`buffer`|`numberOfElements`|`time`|Return|`buffer` 中的值|  
|--------------|------------------------|------------|------------|-----------------------|  
|`NULL`|any|any|`EINVAL`|未修改|  
|不是 `NULL` (指向有效的記憶體)|0|any|`EINVAL`|未修改|  
|非 `NULL`|0< 大小 < 26|any|`EINVAL`|空字串|  
|不是 `NULL`|>= 26|NULL|`EINVAL`|空字串|  
|不是 `NULL`|>= 26|< 0|`EINVAL`|空字串|  
  
## <a name="remarks"></a>備註  
 `ctime_s` 函式會將儲存為 [time_t](../../c-runtime-library/standard-types.md) 結構的時間值轉換為字元字串。 `time` 值通常是透過對 [time](../../c-runtime-library/reference/time-time32-time64.md) 呼叫來取得，這會傳回自國際標準時間 (UTC) 1970 年 1 月 1 日午夜 (00:00:00) 起所經過的秒數。 傳回值字串剛好包含 26 個字元，且具有以下格式：  
  
```  
Wed Jan 02 02:03:55 1980\n\0  
```  
  
 使用 24 小時制。 所有欄位都具有固定寬度。 新行字元 ('\n') 和 null 字元 ('\0') 佔用字串的最後兩個位置。  
  
 已轉換的字元字串也會根據當地時區設定調整。 如需設定當地時間的資訊，請參閱 `time`、[_ftime](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) 和 [localtime32_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md) 函式；如需定義時區環境及全域變數的資訊，請參閱 [_tzset](../../c-runtime-library/reference/tzset.md) 函式。  
  
 `_wctime32_s` 和 `_wctime64_s` 是寬字元版本的 `_ctime32_s` 和 `_ctime64_s`，並會傳回寬字元字串的指標。 否則，`_ctime64_s`、`_wctime32_s` 和 `_wctime64_s` 的行為與 `_ctime32_s` 相同。  
  
 `ctime_s` 是評估為 `_ctime64_s` 的內嵌函式，而 `time_t` 相當於 `__time64_t`。 如果您要強制編譯器將 `time_t` 解譯為舊的 32 位元 `time_t`，您可以定義 `_USE_32BIT_TIME_T`。 如此一來，將導致 `ctime_s` 評估 `_ctime32_s`。 建議您不要這樣做，原因是您的應用程式可能會在 2038 年 1 月 18 日後失敗，且在 64 位元平台上不允許這種定義。  
  
 在 C++ 中，使用這些函式已透過範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tctime_s`|`ctime_s`|`ctime_s`|`_wctime_s`|  
|`_tctime32_s`|`_ctime32_s`|`_ctime32_s`|`_wctime32_s`|  
|`_tctime64_s`|`_ctime64_s`|`_ctime64_s`|`_wctime64_s`|  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`ctime_s`, `_ctime32_s`, `_ctime64_s`|\<time.h>|  
|`_wctime_s`, `_wctime32_s`, `_wctime64_s`|\<time.h> 或 \<wchar.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_wctime_s.c  
/* This program gets the current  
 * time in time_t form and then uses _wctime_s to  
 * display the time in string form.  
 */  
  
#include <time.h>  
#include <stdio.h>  
  
#define SIZE 26  
  
int main( void )  
{  
   time_t ltime;  
   wchar_t buf[SIZE];  
   errno_t err;  
  
   time( &ltime );  
  
   err = _wctime_s( buf, SIZE, &ltime );  
   if (err != 0)  
   {  
      printf("Invalid Arguments for _wctime_s. Error Code: %d\n", err);  
   }  
   wprintf_s( L"The time is %s\n", buf );  
}  
```  
  
## <a name="sample-output"></a>範例輸出  
  
```  
The time is Fri Apr 25 13:03:39 2003  
```  
  
## <a name="see-also"></a>請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime_s、_gmtime32_s、_gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s、_localtime32_s、_localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)