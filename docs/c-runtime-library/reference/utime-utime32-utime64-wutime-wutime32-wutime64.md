---
title: "_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _utime64
- _utime
- _wutime
- _wutime64
- _wutime32
- _utime32
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
- _tutime
- _utime64
- wutime
- utime32
- wutime64
- _utime
- wutime32
- _wutime
- utime
- utime64
- _wutime64
- _utime32
- _tutime64
- _wutime32
dev_langs:
- C++
helpviewer_keywords:
- tutime function
- utime32 function
- utime64 function
- _utime function
- _tutime32 function
- time [C++], file modification
- wutime function
- _wutime function
- _wutime32 function
- _tutime64 function
- _tutime function
- files [C++], modification time
- _wutime64 function
- _utime32 function
- utime function
- _utime64 function
- wutime64 function
- wutime32 function
- tutime64 function
- tutime32 function
ms.assetid: 8d482d40-19b9-4591-bfee-5d7f601d1a9e
caps.latest.revision: 16
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 7d8823bfe5650634d3fb079d2910e98409622ec6
ms.lasthandoff: 02/24/2017

---
# <a name="utime-utime32-utime64-wutime-wutime32-wutime64"></a>_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64
設定檔案修改時間。  
  
## <a name="syntax"></a>語法  
  
```  
int _utime(  
   const char *filename,  
   struct _utimbuf *times   
);  
int _utime32(  
   const char *filename,  
   struct __utimbuf32 *times   
);  
int _utime64(  
   const char *filename,  
   struct __utimbuf64 *times   
);  
int _wutime(  
   const wchar_t *filename,  
   struct _utimbuf *times   
);  
int _wutime32(  
   const wchar_t *filename,  
   struct __utimbuf32 *times   
);  
int _wutime64(  
   const wchar_t *filename,  
   struct __utimbuf64 *times   
);  
```  
  
#### <a name="parameters"></a>參數  
 `filename`  
 包含路徑或檔名之字串的指標。  
  
 `times`  
 預存時間值的指標。  
  
## <a name="return-value"></a>傳回值  
 如果檔案修改時間變更，則所有這些函式都會傳回 0。 –1 的傳回值表示錯誤。 如果傳遞無效參數，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回 -1，並將 `errno` 設為下列其中一個值：  
  
 `EACCES`  
 路徑指定目錄或唯讀檔案  
  
 `EINVAL`  
 無效的 `times` 引數  
  
 `EMFILE`  
 開啟太多檔案 (必須開啟檔案，才能變更其修改時間)  
  
 `ENOENT`  
 找不到路徑或檔名  
  
 如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 如果變更日期晚於 1970 年 1 月 1 日午夜，且早於所使用函式的結束日期，則可以變更檔案的日期。 `_utime` 和 `_wutime` 使用 64 位元時間值，因此結束日期是 3000 年 12 月 31 日 23:59:59 (UTC)。 如果 `_USE_32BIT_TIME_T` 定義成強制執行舊行為，則結束日期是 2038 年 1 月 18 日 23:59:59 (UTC)。 不論是否定義 `_USE_32BIT_TIME_T`，`_utime32` 或 `_wutime32` 都會使用 32 位元時間類型，而且一律會有最早的結束日期。 `_utime64` 或 `_wutime64` 一律會使用 64 位元時間類型，因此這些函式一律會支援較新的結束日期。  
  
## <a name="remarks"></a>備註  
 `_utime` 函式會設定 `filename` 所指定檔案的修改時間。 處理序必須具有檔案的寫入權，才能變更時間。 在 Windows 作業系統中，您可以變更 `_utimbuf` 結構中的存取時間和修改時間。 如果 `times` 是 `NULL` 指標，則修改時間設定為目前當地時間。 否則，`times` 必須指向定義於 SYS\UTIME.H 且類型為 `_utimbuf` 的結構。  
  
 `_utimbuf` 結構會儲存 `_utime` 所使用的檔案存取和修改時間，以變更檔案修改日期。 此結構具有下列都屬於類型 `time_t` 的欄位：  
  
 `actime`  
 檔案存取的時間  
  
 `modtime`  
 檔案修改的時間  
  
 特定版本的 `_utimbuf` 結構 (`_utimebuf32` 和 `__utimbuf64`) 是使用 32 位元和 64 位元版本的時間類型所定義。 這些是用在此函式的 32 位元和 64 位元特定版本。 除非定義 `_USE_32BIT_TIME_T`，否則 `_utimbuf` 本身預設會使用 64 位元時間類型。  
  
 `_utime` 等同於 `_futime`，不同之處在於 `_utime` 的 `filename` 引數是檔案的檔名或路徑，而不是開啟檔案的檔案描述元。  
  
 `_wutime` 是寬字元版本的 `_utime`；`filename` 的 `_wutime` 引數是寬字元字串。 除此之外，這些函式的行為相同。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tutime`|`_utime`|`_utime`|`_wutime`|  
|`_tutime32`|`_utime32`|`_utime32`|`_wutime32`|  
|`_tutime64`|`_utime64`|`_utime64`|`_wutime64`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要標頭|選擇性標頭|  
|-------------|----------------------|----------------------|  
|`_utime`, `_utime32`, `_utime64`|\<sys/utime.h>|\<errno.h>|  
|`_utime64`|\<sys/utime.h>|\<errno.h>|  
|`_wutime`|\<utime.h> 或 \<wchar.h>|\<errno.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 此程式會使用 `_utime`，以將檔案修改時間設為目前時間。  
  
```  
// crt_utime.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <sys/types.h>  
#include <sys/utime.h>  
#include <time.h>  
  
int main( void )  
{  
   struct tm tma = {0}, tmm = {0};  
   struct _utimbuf ut;  
  
   // Fill out the accessed time structure  
   tma.tm_hour = 12;  
   tma.tm_isdst = 0;  
   tma.tm_mday = 15;  
   tma.tm_min = 0;  
   tma.tm_mon = 0;  
   tma.tm_sec = 0;  
   tma.tm_year = 103;  
  
   // Fill out the modified time structure  
   tmm.tm_hour = 12;  
   tmm.tm_isdst = 0;  
   tmm.tm_mday = 15;  
   tmm.tm_min = 0;  
   tmm.tm_mon = 0;  
   tmm.tm_sec = 0;  
   tmm.tm_year = 102;  
  
   // Convert tm to time_t  
   ut.actime = mktime(&tma);  
   ut.modtime = mktime(&tmm);  
  
   // Show file time before and after  
   system( "dir crt_utime.c" );  
   if( _utime( "crt_utime.c", &ut ) == -1 )  
      perror( "_utime failed\n" );  
   else  
      printf( "File time modified\n" );  
   system( "dir crt_utime.c" );  
}  
```  
  
## <a name="sample-output"></a>範例輸出  
  
```  
Volume in drive C has no label.  
 Volume Serial Number is 9CAC-DE74  
  
 Directory of C:\test  
  
01/09/2003  05:38 PM               935 crt_utime.c  
               1 File(s)            935 bytes  
               0 Dir(s)  20,742,955,008 bytes free  
File time modified  
 Volume in drive C has no label.  
 Volume Serial Number is 9CAC-DE74  
  
 Directory of C:\test  
  
01/15/2002  12:00 PM               935 crt_utime.c  
               1 File(s)            935 bytes  
               0 Dir(s)  20,742,955,008 bytes free  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [_futime、_futime32、_futime64](../../c-runtime-library/reference/futime-futime32-futime64.md)   
 [gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [_stat、_wstat 函式](../../c-runtime-library/reference/stat-functions.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)
