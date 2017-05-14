---
title: "_stat、_stat32、_stat64、_stati64、_stat32i64、_stat64i32、_wstat、_wstat32、_wstat64、_wstati64、_wstat32i64、_wstat64i32 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wstat64
- _stati64
- _stat32
- _stat32i64
- _stat
- _wstati64
- _wstat32
- _wstat64i32
- _wstat
- _stat64
- _stat64i32
- _wstat32i64
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
- tstat32
- tstat
- _tstat64i32
- tstati64
- _wstat64
- _wstat32
- wstati64
- tstat64
- _stati64
- _wstat
- wstat64i32
- stat32i64
- tstat32i64
- _tstat
- _wstati64
- _tstati64
- _wstat32i64
- wstat32
- _wstat64i32
- _stat
- _tstat32
- stat64i32
- wstat64
- stat
- _stat32i64
- _stat32
- stati64
- wstat
- _stat64i32
- stat32
- _tstat32i64
- tstat64i32
- _tstat64
- _stat64
- stat/_stat
- stat/_stat32
- stat/_stat64
- stat/_stati64
- stat/_stat32i64
- stat/_stat64i32
- stat/_wstat
- stat/_wstat32
- stat/_wstat64
- stat/_wstati64
- stat/_wstat32i64
- stat/_wstat64i32
dev_langs:
- C++
helpviewer_keywords:
- files [C++], status information
- _stat function
- _wstat function
- _stat64i32 function
- tstat function
- _tstat64i32 function
- _stati64 function
- _stat64 function
- tstati64 function
- wstati64 function
- wstat64 function
- _wstat64i32 function
- _tstat32i64 function
- _stat32i64 function
- stat function
- status of files
- _tstat32 function
- tstat64 function
- _wstat64 function
- _tstat function
- _stat32 function
- wstat function
- _wstat32i64 function
- _tstati64 function
- _wstat32 function
- stat64 function
- stati64 function
- _wstati64 function
- _tstat64 function
- files [C++], getting status information
ms.assetid: 99a75ae6-ff26-47ad-af70-5ea7e17226a5
caps.latest.revision: 26
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
ms.openlocfilehash: 1c3fc1e6ee3ca15d610d2c25ad38eedb795d0ebf
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="stat-stat32-stat64-stati64-stat32i64-stat64i32-wstat-wstat32-wstat64-wstati64-wstat32i64-wstat64i32"></a>_stat、_stat32、_stat64、_stati64、_stat32i64、_stat64i32、_wstat、_wstat32、_wstat64、_wstati64、_wstat32i64、_wstat64i32
取得檔案的狀態資訊。  
  
## <a name="syntax"></a>語法  
  
```  
int _stat(  
   const char *path,  
   struct _stat *buffer   
);  
int _stat32(  
   const char *path,  
   struct __stat32 *buffer   
);  
int _stat64(  
   const char *path,  
   struct __stat64 *buffer   
);  
int _stati64(  
   const char *path,  
   struct _stati64 *buffer   
);  
int _stat32i64(  
   const char *path,  
   struct _stat32i64 *buffer   
);  
int _stat64i32(  
   const char *path,  
   struct _stat64i32 *buffer   
);  
int _wstat(  
   const wchar_t *path,  
   struct _stat *buffer   
);  
int _wstat32(  
   const wchar_t *path,  
   struct __stat32 *buffer   
);  
int _wstat64(  
   const wchar_t *path,  
   struct __stat64 *buffer   
);  
int _wstati64(  
   const wchar_t *path,  
   struct _stati64 *buffer   
);  
int _wstat32i64(  
   const wchar_t *path,  
   struct _stat32i64 *buffer   
);  
int _wstat64i32(  
   const wchar_t *path,  
   struct _stat64i32 *buffer   
);  
```  
  
#### <a name="parameters"></a>參數  
 `path`  
 包含現有檔案或目錄路徑的字串指標。  
  
 `buffer`  
 儲存結果的結構指標。  
  
## <a name="return-value"></a>傳回值  
 上述每個函式會在取得檔案狀態資訊時傳回 0。 傳回值-1 表示錯誤，在此情況下`errno`設`ENOENT`，指出，檔案名稱或路徑找不到。 傳回值 `EINVAL` 表示參數無效，在此情況下也會將 `errno` 設定為 `EINVAL` 。  
  
 如需這個傳回碼及其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 如果是 1970 年 1 月 1 日午夜到 3000 年 12 月 31 日 23:59:59 (UTC) 的檔案，則會在檔案上表示日期戳記；除非您使用 `_stat32` 或 `_wstat32`，或者已定義 `_USE_32BIT_TIME_T`，在此情況下，只能表示 2038 年 1 月 18 日 23:59:59 (UTC) 以前的日期。  
  
## <a name="remarks"></a>備註  
 `_stat` 函式會取得 `path` 所指定之檔案或目錄的相關資訊，並將其儲存在 `buffer`所指向的結構中。 `_stat` 會根據目前使用中的多位元組字碼頁，自動將多位元組字元字串引數處理為適當且可辨識的多位元組字元序列。  
  
 `_wstat` 是寬字元版本的 `_stat`； `path` 的 `_wstat` 引數是寬字元字串。 `_wstat` 與 `_stat` 的運作方式完全相同，不同之處在於 `_wstat` 不會處理多位元組字元字串。  
  
 這些函式的各種版本支援 32 位元或 64 位元時間類型，以及 32 位元或 64 位元檔案長度。 第一個數值後置字元 (`32` 或 `64`) 表示所使用的時間類型大小，第二個後置字元為 `i32` 或 `i64`，表示檔案大小是以 32 位元或 64 位元整數來表示。  
  
 `_stat` 相當於 `_stat64i32`，且 `struct``_stat` 包含 64 位元時間。 This is true unless `_USE_32BIT_TIME_T` is defined, in which case the old behavior is in effect; `_stat` uses a 32-bit time, and `struct``_stat` contains a 32-bit time. 對於 `_stati64`也是如此。  
  
> [!NOTE]
>  `_wstat` 不適用於 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] 符號連結。 在這些情況下， `_wstat` 一律會回報檔案大小為 0。 `_stat` 則適用於符號連結。  
  
 這個函式會驗證它的參數。 如果 `path` 或 `buffer` 為 `NULL`，則會叫用無效的參數處理常式，如 [Parameter Validation](../../c-runtime-library/parameter-validation.md)所指向的結構中。  
  
### <a name="time-type-and-file-length-type-variations-of-stat"></a>_stat 的時間類型和檔案長度類型版本  
  
|函式|是否已定義 _USE_32BIT_TIME_T？|時間類型|檔案長度類型|  
|---------------|------------------------------------|---------------|----------------------|  
|`_stat`, `_wstat`|未定義|64 位元|32 位元|  
|`_stat`, `_wstat`|已定義|32 位元|32 位元|  
|`_stat32`, `_wstat32`|不會受到巨集定義的影響|32 位元|32 位元|  
|`_stat64`, `_wstat64`|不會受到巨集定義的影響|64 位元|64 位元|  
|`_stati64`, `_wstati64`|未定義|64 位元|64 位元|  
|`_stati64`, `_wstati64`|已定義|32 位元|64 位元|  
|`_stat32i64`, `_wstat32i64`|不會受到巨集定義的影響|32 位元|64 位元|  
|`_stat64i32`, `_wstat64i32`|不會受到巨集定義的影響|64 位元|32 位元|  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tstat`|`_stat`|`_stat`|`_wstat`|  
|`_tstat64`|`_stat64`|`_stat64`|`_wstat64`|  
|`_tstati64`|`_stati64`|`_stati64`|`_wstati64`|  
|`_tstat32i64`|`_stat32i64`|`_stat32i64`|`_wstat32i64`|  
|`_tstat64i32`|`_stat64i32`|`_stat64i32`|`_wstat64i32`|  
  
 在 SYS\STAT.H 中定義的 `_stat` 結構包含下列欄位。  
  
 `st_gid`  
 擁有檔案 (UNIX 特定) 之群組的數值識別碼。這個欄位在 Windows 系統上一律為零。 重新導向的檔案會歸類為 Windows 檔案。  
  
 `st_atime`  
 檔案的上次存取時間。 適用於 NTFS，但不適用 FAT 格式的磁碟機。  
  
 `st_ctime`  
 檔案的建立時間。 適用於 NTFS，但不適用 FAT 格式的磁碟機。  
  
 `st_dev`  
 內含檔案之磁碟的磁碟機數目 (與 `st_rdev`相同)。  
  
 `st_ino`  
 檔案 (UNIX 特定) 的資訊節點數目 ( `inode`)。 在 UNIX 檔案系統上， `inode` 會描述檔案日期和時間戳記、權限，以及內容。 當檔案彼此永久連結時，這些檔案會共用相同的 `inode`。 `inode`及之後的 `st_ino`對 FAT、HPFS 或 NTFS 檔案系統沒有意義。  
  
 `st_mode`  
 檔案模式資訊的位元遮罩。 如果 `_S_IFDIR` 指定目錄，會設定 `path` 位元；如果 `_S_IFREG` 指定一般檔案或裝置，會設定 `path` 位元。 使用者讀取/寫入位元會根據檔案的權限模式進行設定；使用者執行位元會根據副檔名進行設定。  
  
 `st_mtime`  
 檔案的上次修改時間。  
  
 `st_nlink`  
 在非 NTFS 檔案系統上一律為 1。  
  
 `st_rdev`  
 內含檔案之磁碟的磁碟機數目 (與 `st_dev`相同)。  
  
 `st_size`  
 檔案大小 (以位元組為單位)；後置字元為 `i64` 的版本使用 64 位元整數**。**  
  
 `st_uid`  
 擁有檔案 (UNIX 特定) 之使用者的數值識別碼。 這個欄位在 Windows 系統上一律為零。 重新導向的檔案會歸類為 Windows 檔案。  
  
 如果 `path` 參考裝置， `st_size`結構中的 `st_dev`、各種時間欄位、 `st_rdev` 和 `_stat` 都沒有意義。 因為 STAT.H 使用在 TYPES.H 中定義的 [_dev_t](../../c-runtime-library/standard-types.md) 類型，所以您必須在程式碼中的 STAT.H 之前包含 TYPES.H。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|選擇性標頭|  
|-------------|---------------------|----------------------|  
|`_stat`, `_stat32`, `_stat64`, `_stati64`, `_stat32i64`, `_stat64i32`|\<sys/types.h>，後面接著 \<sys/stat.h>|\<errno.h>|  
|`_wstat`, `_wstat32`, `_wstat64`, `_wstati64`, `_wstat32i64`, `_wstat64i32`|\<sys/types.h>，後面接著 \<sys/stat.h> 或 \<wchar.h>|\<errno.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_stat.c  
// This program uses the _stat function to  
// report information about the file named crt_stat.c.  
  
#include <time.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
   struct _stat buf;  
   int result;  
   char timebuf[26];  
   char* filename = "crt_stat.c";  
   errno_t err;  
  
   // Get data associated with "crt_stat.c":   
   result = _stat( filename, &buf );  
  
   // Check if statistics are valid:   
   if( result != 0 )  
   {  
      perror( "Problem getting information" );  
      switch (errno)  
      {  
         case ENOENT:  
           printf("File %s not found.\n", filename);  
           break;  
         case EINVAL:  
           printf("Invalid parameter to _stat.\n");  
           break;  
         default:  
           /* Should never be reached. */  
           printf("Unexpected error in _stat.\n");  
      }  
   }  
   else  
   {  
      // Output some of the statistics:   
      printf( "File size     : %ld\n", buf.st_size );  
      printf( "Drive         : %c:\n", buf.st_dev + 'A' );  
      err = ctime_s(timebuf, 26, &buf.st_mtime);  
      if (err)  
      {  
         printf("Invalid arguments to ctime_s.");  
         exit(1);  
      }  
      printf( "Time modified : %s", timebuf );  
   }  
}  
```  
  
```Output  
File size     : 732  
Drive         : C:  
Time modified : Thu Feb 07 14:39:36 2002  
```  
  
## <a name="see-also"></a>另請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [_access、_waccess](../../c-runtime-library/reference/access-waccess.md)   
 [_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)
