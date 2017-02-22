---
title: "_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fstat32"
  - "_fstat64"
  - "_fstati64"
  - "_fstat"
  - "_fstat64i32"
  - "_fstat32i64"
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
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_fstat32i64"
  - "fstat"
  - "fstat64i32"
  - "_fstat64"
  - "_fstati64"
  - "fstat64"
  - "_fstat32"
  - "fstat32i64"
  - "fstati64"
  - "_fstat"
  - "fstat32"
  - "_fstat64i32"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fstat64 函式"
  - "fstati64 函式"
  - "_fstat64i32 函式"
  - "_fstat32i64 函式"
  - "_fstat32 函式"
  - "檔案資訊"
  - "fstat64i32 函式"
  - "fstat32 函式"
  - "fstat 函式"
  - "fstat64 函式"
  - "_fstat 函式"
  - "_fstati64 函式"
  - "fstat32i64 函式"
ms.assetid: 088f5e7a-9636-4cf7-ab8e-e28d2aa4280a
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# _fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得開啟的檔案的相關資訊。  
  
## 語法  
  
```  
int _fstat(   
   int fd,  
   struct _stat *buffer   
);  
int _fstat32(   
   int fd,  
   struct __stat32 *buffer   
);  
int _fstat64(   
   int fd,  
   struct __stat64 *buffer   
);  
int _fstati64(   
   int fd,  
   struct _stati64 *buffer   
);  
int _fstat32i64(   
   int fd,  
   struct _stat32i64 *buffer   
);  
int _fstat64i32(   
   int fd,  
   struct _stat64i32 *buffer   
);  
```  
  
#### 參數  
 `fd`  
 已開啟之檔案的檔案描述項。  
  
 `buffer`  
 要儲存結果的結構指標。  
  
## 傳回值  
 如果取得檔案狀態資訊，傳回 0。 –1 的傳回值表示錯誤。 如果檔案描述項無效，或 `buffer` 是 `NULL`, 、 無效參數處理常式叫用時，所述 [參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行 `errno` 設為 `EBADF`, 、 無效的檔案描述元，或為 `EINVAL`, ，如果 `buffer` 是 `NULL`。  
  
## 備註  
 `_fstat` 函式會取得資訊開啟與相關聯的檔案 `fd` 並將它儲存在結構中所指 `buffer`。`_stat` SYS\\Stat.h 中, 定義的結構包含下列欄位。  
  
 `st_atime`  
 最後一個檔案存取時間。  
  
 `st_ctime`  
 建立檔案的時間。  
  
 `st_dev`  
 如果裝置 `fd`，否則為 0。  
  
 `st_mode`  
 檔案模式資訊的位元遮罩。`_S_IFCHR` 如果位元設定 `fd` 指的是裝置。`_S_IFREG` 如果位元設定 `fd` 指的是一般的檔案。 根據檔案的權限模式設定的讀取\/寫入位元。`_S_IFCHR` 和其他常數 SYS\\Stat.h 中定義。  
  
 `st_mtime`  
 檔案的上次修改時間。  
  
 `st_nlink`  
 在非 NTFS 檔案系統上一律為 1。  
  
 `st_rdev`  
 如果裝置 `fd`，否則為 0。  
  
 `st_size`  
 以位元組為單位的檔案大小。  
  
 如果 `fd` 到裝置，是指 `st_atime`, ，`st_ctime`, ，`st_mtime`, ，和 `st_size` 欄位並沒有意義。  
  
 因為使用 Stat.h [\_dev\_t](../../c-runtime-library/standard-types.md) 輸入，定義在 Types.h，您必須包含 Types.h Stat.h 之前程式碼中。  
  
 `_fstat64`, 它會使用 `__stat64` 結構，可讓總 23:59:59，3000 年 12 月 31 日 UTC 表示的檔案建立日期，而其他函式只能代表 23:59:59 2038 年 1 月 18 日 UTC 日期。 午夜過後，1970 年 1 月 1 日是所有這些函式的日期範圍的下限。  
  
 這些函式的各種支援 32 位元或 64 位元的時間型別和 32 位元或 64 位元檔案長度。 第一個數值後置字元 \(`32` 或 `64`\) 表示所使用的時間類型大小，第二個後置字元為 `i32` 或 `i64`，表示檔案大小是以 32 位元或 64 位元整數來表示。  
  
 `_fstat` 相當於 `_fstat64i32`, ，和 `struct``_stat` 包含 64 位元時間。 這是 true 除非 `_USE_32BIT_TIME_T` 定義在此情況下舊的行為是生效; `_fstat` 使用 32 位元的時間和 `struct``_stat` 包含 32 位元時間。 這也適用於 `_fstati64`。  
  
### \_stat 的時間類型和檔案長度類型版本  
  
|函式|是否已定義 \_USE\_32BIT\_TIME\_T？|時間類型|檔案長度類型|  
|--------|----------------------------------|----------|------------|  
|`_fstat`|未定義|64 位元|32 位元|  
|`_fstat`|已定義|32 位元|32 位元|  
|`_fstat32`|不會受到巨集定義的影響|32 位元|32 位元|  
|`_fstat64`|不會受到巨集定義的影響|64 位元|64 位元|  
|`_fstati64`|未定義|64 位元|64 位元|  
|`_fstati64`|已定義|32 位元|64 位元|  
|`_fstat32i64`|不會受到巨集定義的影響|32 位元|64 位元|  
|`_fstat64i32`|不會受到巨集定義的影響|64 位元|32 位元|  
  
## 需求  
  
|函式|必要的標頭|  
|--------|-----------|  
|`_fstat`|\<.h \> 和 \< s \>|  
|`_fstat32`|\<.h \> 和 \< s \>|  
|`_fstat64`|\<.h \> 和 \< s \>|  
|`_fstati64`|\<.h \> 和 \< s \>|  
|`_fstat32i64`|\<.h \> 和 \< s \>|  
|`_fstat64i32`|\<.h \> 和 \< s \>|  
  
 如需相容性詳細資訊，請參閱簡介中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_fstat.c  
// This program uses _fstat to report  
// the size of a file named F_STAT.OUT.  
  
#include <io.h>  
#include <fcntl.h>  
#include <time.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
#include <errno.h>  
#include <share.h>  
  
int main( void )  
{  
   struct _stat buf;  
   int fd, result;  
   char buffer[] = "A line to output";  
   char timebuf[26];  
   errno_t err;  
  
   _sopen_s( &fd,  
             "f_stat.out",  
             _O_CREAT | _O_WRONLY | _O_TRUNC,  
             _SH_DENYNO,  
             _S_IREAD | _S_IWRITE );  
   if( fd != -1 )  
      _write( fd, buffer, strlen( buffer ) );  
  
   // Get data associated with "fd":   
   result = _fstat( fd, &buf );  
  
   // Check if statistics are valid:   
   if( result != 0 )  
   {  
      if (errno == EBADF)  
        printf( "Bad file descriptor.\n" );  
      else if (errno == EINVAL)  
        printf( "Invalid argument to _fstat.\n" );  
   }  
   else  
   {  
      printf( "File size     : %ld\n", buf.st_size );  
      err = ctime_s(timebuf, 26, &buf.st_mtime);  
      if (err)  
      {  
         printf("Invalid argument to ctime_s.");  
         exit(1);  
      }  
      printf( "Time modified : %s", timebuf );  
   }  
   _close( fd );  
}  
```  
  
```Output  
檔案大小︰ 16 次修改時間︰ 星期三 5 月 07 日 15:25:11 2003年  
```  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [\_access、\_waccess](../../c-runtime-library/reference/access-waccess.md)   
 [\_chmod、\_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [\_filelength、\_filelengthi64](../../c-runtime-library/reference/filelength-filelengthi64.md)   
 [\_stat、\_wstat 函式](../../c-runtime-library/reference/stat-functions.md)