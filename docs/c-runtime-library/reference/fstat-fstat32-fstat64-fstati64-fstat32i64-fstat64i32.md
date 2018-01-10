---
title: "_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fstat32
- _fstat64
- _fstati64
- _fstat
- _fstat64i32
- _fstat32i64
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _fstat32i64
- fstat
- fstat64i32
- _fstat64
- _fstati64
- fstat64
- _fstat32
- fstat32i64
- fstati64
- _fstat
- fstat32
- _fstat64i32
dev_langs: C++
helpviewer_keywords:
- _fstat64 function
- fstati64 function
- _fstat64i32 function
- _fstat32i64 function
- _fstat32 function
- file information
- fstat64i32 function
- fstat32 function
- fstat function
- fstat64 function
- _fstat function
- _fstati64 function
- fstat32i64 function
ms.assetid: 088f5e7a-9636-4cf7-ab8e-e28d2aa4280a
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d2993016e9c6b3a4ea7d47ba8071fab1267e483f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32"></a>_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32
取得開啟之檔案的相關資訊。  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 `fd`  
 已開啟之檔案的檔案描述項。  
  
 `buffer`  
 儲存結果的結構指標。  
  
## <a name="return-value"></a>傳回值  
 如果取得檔案狀態資訊，則傳回 0。 傳回值-1 表示錯誤。 如果檔案描述元無效或 `buffer` 為 `NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，在檔案描述元無效的情形中，`errno` 會設為 `EBADF`，如果 `buffer` 為 `NULL`，則會設為 `EINVAL`。  
  
## <a name="remarks"></a>備註  
 `_fstat` 函式會取得與 `fd` 相關聯之開啟的檔案的相關資訊，並將它儲存在 `buffer` 結構中。 定義於 SYS\Stat.h 中，`_stat` 結構包含下列欄位。  
  
 `st_atime`  
 最後存取檔案的時間。  
  
 `st_ctime`  
 建立檔案的時間。  
  
 `st_dev`  
 如果是裝置，則為 `fd`，否則為 0。  
  
 `st_mode`  
 檔案模式資訊的位元遮罩。 如果 `fd` 指的是裝置，則會設定 `_S_IFCHR` 位元。 如果 `fd` 指的是一般檔案，則會設定 `_S_IFREG` 位元。 讀取/寫入位元會根據檔案的權限模式設定。 `_S_IFCHR` 和其他常數於 SYS\Stat.h 中定義。  
  
 `st_mtime`  
 檔案的上次修改時間。  
  
 `st_nlink`  
 在非 NTFS 檔案系統上一律為 1。  
  
 `st_rdev`  
 如果是裝置，則為 `fd`，否則為 0。  
  
 `st_size`  
 檔案大小，以位元組為單位。  
  
 如果 `fd` 指的是裝置，則 `st_atime`、`st_ctime`、`st_mtime`和`st_size` 欄位並沒有意義。  
  
 因為 Stat.h 使用在 Types.h 中定義的 [_dev_t](../../c-runtime-library/standard-types.md) 類型，所以您必須在程式碼中的 Stat.h 之前包含 Types.h。  
  
 使用 `__stat64` 結構的 `_fstat64`，允許表示至3000 年 12 月 31 日 23:59:59 UTC 為止的日期；而其他函式只能表示至 2038 年 1 月 18 日23:59:59 UTC 的日期。 1970 年 1 月 1 日午夜是所有這些函式的日期範圍下限。  
  
 這些函式的變化支援 32 位元或 64 位元時間類型，以及 32 位元或 64 位元檔案長度。 第一個數值後置字元 (`32` 或 `64`) 表示所使用的時間類型大小，第二個後置字元為 `i32` 或 `i64`，表示檔案大小是以 32 位元或 64 位元整數來表示。  
  
 `_fstat` 相當於 `_fstat64i32`，且 `struct _stat` 包含 64 位元時間。 上述情況只有在定義 `_USE_32BIT_TIME_T` 時才不成立，在此情況下，會採用舊版行為，也就是 `_fstat` 使用 32 位元時間，且 `struct _stat` 包含 32 位元時間。 對於 `_fstati64` 也是如此。  
  
### <a name="time-type-and-file-length-type-variations-of-stat"></a>_stat 的時間類型和檔案長度類型版本  
  
|函式|是否已定義 _USE_32BIT_TIME_T？|時間類型|檔案長度類型|  
|---------------|------------------------------------|---------------|----------------------|  
|`_fstat`|未定義|64 位元|32 位元|  
|`_fstat`|已定義|32 位元|32 位元|  
|`_fstat32`|不會受到巨集定義的影響|32 位元|32 位元|  
|`_fstat64`|不會受到巨集定義的影響|64 位元|64 位元|  
|`_fstati64`|未定義|64 位元|64 位元|  
|`_fstati64`|已定義|32 位元|64 位元|  
|`_fstat32i64`|不會受到巨集定義的影響|32 位元|64 位元|  
|`_fstat64i32`|不會受到巨集定義的影響|64 位元|32 位元|  
  
## <a name="requirements"></a>需求  
  
|功能|必要的標頭|  
|--------------|---------------------|  
|`_fstat`|\<sys/stat.h> 和 \<sys/types.h>|  
|`_fstat32`|\<sys/stat.h> 和 \<sys/types.h>|  
|`_fstat64`|\<sys/stat.h> 和 \<sys/types.h>|  
|`_fstati64`|\<sys/stat.h> 和 \<sys/types.h>|  
|`_fstat32i64`|\<sys/stat.h> 和 \<sys/types.h>|  
|`_fstat64i32`|\<sys/stat.h> 和 \<sys/types.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
  
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
File size     : 16  
Time modified : Wed May 07 15:25:11 2003  
```  
  
## <a name="see-also"></a>請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [_access、_waccess](../../c-runtime-library/reference/access-waccess.md)   
 [_chmod、_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_filelength、_filelengthi64](../../c-runtime-library/reference/filelength-filelengthi64.md)   
 [_stat、_wstat 函式](../../c-runtime-library/reference/stat-functions.md)