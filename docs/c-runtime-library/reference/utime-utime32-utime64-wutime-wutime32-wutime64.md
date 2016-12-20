---
title: "_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_utime64"
  - "_utime"
  - "_wutime"
  - "_wutime64"
  - "_wutime32"
  - "_utime32"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-time-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_tutime"
  - "_utime64"
  - "wutime"
  - "utime32"
  - "wutime64"
  - "_utime"
  - "wutime32"
  - "_wutime"
  - "utime"
  - "utime64"
  - "_wutime64"
  - "_utime32"
  - "_tutime64"
  - "_wutime32"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "tutime 函式"
  - "utime32 函式"
  - "utime64 函式"
  - "_utime 函式"
  - "_tutime32 函式"
  - "時間 [C++]，檔案修改"
  - "wutime 函式"
  - "_wutime 函式"
  - "_wutime32 函式"
  - "_tutime64 函式"
  - "_tutime 函式"
  - "檔案 [C++]，修改時間"
  - "_wutime64 函式"
  - "_utime32 函式"
  - "utime 函式"
  - "_utime64 函式"
  - "wutime64 函式"
  - "wutime32 函式"
  - "tutime64 函式"
  - "tutime32 函式"
ms.assetid: 8d482d40-19b9-4591-bfee-5d7f601d1a9e
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _utime、_utime32、_utime64、_wutime、_wutime32、_wutime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定檔案修改時間。  
  
## 語法  
  
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
  
#### 參數  
 `filename`  
 包含的路徑或檔名的字串指標。  
  
 `times`  
 指標會儲存時間值。  
  
## 傳回值  
 如果變更檔案修改時間，這些函式會傳回 0。 –1 的傳回值表示錯誤。 如果傳遞了無效的參數，則無效參數處理常式叫用時，所述 [參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函數會傳回\-1 和 `errno` 設為下列值之一︰  
  
 `EACCES`  
 指定目錄或唯讀檔案的路徑  
  
 `EINVAL`  
 無效 `times` 引數  
  
 `EMFILE`  
 太多開啟的檔案 （若要變更其修改的時間必須開啟檔案）  
  
 `ENOENT`  
 路徑或找不到的檔案名稱  
  
 請參閱 [\_doserrno，errno，\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 如需有關這些功能和其他的詳細資訊，傳回碼。  
  
 如果變更日期是 1970 年 1 月 1 日的午夜之後，以及使用的函式的結束日期之前，可以變更日期的檔案。`_utime` 和 `_wutime` 23:59:59，3000 年 12 月 31 日 UTC 結束日期是使用 64 位元時間值。 如果 `_USE_32BIT_TIME_T` 定義強制舊的行為，請結束日期是 23:59:59 2038 年 1 月 18 日 UTC。`_utime32` 或 `_wutime32` 使用 32 位元時間型別，而不論是否 `_USE_32BIT_TIME_T` 定義，且一定會較早的結束日期。`_utime64` 或 `_wutime64` 一律使用 64 位元 time 類型一樣，因此這些函式一律會支援較新的結束日期。  
  
## 備註  
 `_utime` 函式會將所指定的檔案的修改時間 `filename`*。*處理程序必須有檔案寫入存取，才能變更的時間。 在 Windows 作業系統中，您可以變更存取時間與修改的時間在 `_utimbuf` 結構。 如果 `times` 是 `NULL` 指標，修改時間設定為目前的當地時間。 否則， `times` 類型的結構必須指向 `_utimbuf`, SYS\\UTIME 中定義。H.  
  
 `_utimbuf` 結構會儲存所使用的檔案存取和修改時間 `_utime` 以變更檔案修改日期。 此結構具有下列欄位，都屬於型別 `time_t`:  
  
 `actime`  
 檔案存取時間  
  
 `modtime`  
 檔案修改時間  
  
 特定版本的 `_utimbuf` 結構 \(`_utimebuf32` 和 `__utimbuf64`\) 都使用 32 位元和 64 位元版本的階段型別定義。 這些用在 32 位元和 64 位元特定版本，此函式。`_utimbuf` 根據預設本身會使用 64 位元時間型別，除非 `_USE_32BIT_TIME_T` 定義。  
  
 `_utime` 等同於 `_futime` 不同之處在於 `filename` 引數的 `_utime` 是檔案名稱或檔案，而不是檔案描述元，開啟檔案的路徑。  
  
 `_wutime` 是寬字元版本的 `_utime`；`filename` 的 `_wutime` 引數是寬字元字串。 除此之外，這些函式的行為相同。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tutime`|`_utime`|`_utime`|`_wutime`|  
|`_tutime32`|`_utime32`|`_utime32`|`_wutime32`|  
|`_tutime64`|`_utime64`|`_utime64`|`_wutime64`|  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_utime`, `_utime32`, `_utime64`|\< \> sys\/utime.h|\<errno.h\>|  
|`_utime64`|\< \> sys\/utime.h|\<errno.h\>|  
|`_wutime`|\< utime.h \> 或 \< wchar.h \>|\<errno.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 此程式會使用 `_utime` 檔案修改時間設定為目前的時間。  
  
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
  
## 範例輸出  
  
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
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime、\_ctime32、\_ctime64、\_wctime、\_wctime32、\_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [\_fstat、\_fstat32、\_fstat64、\_fstati64、\_fstat32i64、\_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [\_ftime、\_ftime32、\_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [\_futime、\_futime32、\_futime64](../../c-runtime-library/reference/futime-futime32-futime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime，\_localtime32，\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [\_stat、\_wstat 函式](../../c-runtime-library/reference/stat-functions.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)