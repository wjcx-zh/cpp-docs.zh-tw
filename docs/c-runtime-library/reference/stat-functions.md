---
title: "_stat、_stat32、_stat64、_stati64、_stat32i64、_stat64i32、_wstat、_wstat32、_wstat64、_wstati64、_wstat32i64、_wstat64i32 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wstat64"
  - "_stati64"
  - "_stat32"
  - "_stat32i64"
  - "_stat"
  - "_wstati64"
  - "_wstat32"
  - "_wstat64i32"
  - "_wstat"
  - "_stat64"
  - "_stat64i32"
  - "_wstat32i64"
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
  - "tstat32"
  - "tstat"
  - "_tstat64i32"
  - "tstati64"
  - "_wstat64"
  - "_wstat32"
  - "wstati64"
  - "tstat64"
  - "_stati64"
  - "_wstat"
  - "wstat64i32"
  - "stat32i64"
  - "tstat32i64"
  - "_tstat"
  - "_wstati64"
  - "_tstati64"
  - "_wstat32i64"
  - "wstat32"
  - "_wstat64i32"
  - "_stat"
  - "_tstat32"
  - "stat64i32"
  - "wstat64"
  - "stat"
  - "_stat32i64"
  - "_stat32"
  - "stati64"
  - "wstat"
  - "_stat64i32"
  - "stat32"
  - "_tstat32i64"
  - "tstat64i32"
  - "_tstat64"
  - "_stat64"
  - "stat/_stat"
  - "stat/_stat32"
  - "stat/_stat64"
  - "stat/_stati64"
  - "stat/_stat32i64"
  - "stat/_stat64i32"
  - "stat/_wstat"
  - "stat/_wstat32"
  - "stat/_wstat64"
  - "stat/_wstati64"
  - "stat/_wstat32i64"
  - "stat/_wstat64i32"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "檔案 [C++]，狀態資訊"
  - "_stat 函式"
  - "_wstat 函式"
  - "_stat64i32 函式"
  - "tstat 函式"
  - "_tstat64i32 函式"
  - "_stati64 函式"
  - "_stat64 函式"
  - "tstati64 函式"
  - "wstati64 函式"
  - "wstat64 函式"
  - "_wstat64i32 函式"
  - "_tstat32i64 函式"
  - "_stat32i64 函式"
  - "stat 函式"
  - "檔案的狀態"
  - "_tstat32 函式"
  - "tstat64 函式"
  - "_wstat64 函式"
  - "_tstat 函式"
  - "_stat32 函式"
  - "wstat 函式"
  - "_wstat32i64 函式"
  - "_tstati64 函式"
  - "_wstat32 函式"
  - "stat64 函式"
  - "stati64 函式"
  - "_wstati64 函式"
  - "_tstat64 函式"
  - "檔案 [C++]，取得狀態資訊"
ms.assetid: 99a75ae6-ff26-47ad-af70-5ea7e17226a5
caps.latest.revision: 26
caps.handback.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _stat、_stat32、_stat64、_stati64、_stat32i64、_stat64i32、_wstat、_wstat32、_wstat64、_wstati64、_wstat32i64、_wstat64i32
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得檔案的狀態資訊。  
  
## 語法  
  
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
  
#### 參數  
 `path`  
 包含現有檔案或目錄路徑的字串指標。  
  
 `buffer`  
 儲存結果的結構指標。  
  
## 傳回值  
 上述每個函式會在取得檔案狀態資訊時傳回 0。 傳回值 \-1 表示發生錯誤，在此情況下會將 `errno` 設定為 `ENOENT`，表示找不到檔案名稱或路徑。 傳回值 `EINVAL` 表示參數無效，在此情況下也會將 `errno` 設定為 `EINVAL`。  
  
 如需這個及其他傳回碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 可以表示檔案的日期戳記，如果它是比 1970 年 1 月 1 日的午夜和 23:59:59，3000 年 12 月 31 日 UTC 之前, 的更新版本，除非您使用 `_stat32` 或 `_wstat32`, ，或已定義 `_USE_32BIT_TIME_T`, ，在此情況下只到 23:59:59 2038 年 1 月 18 日 UTC 代表的日期。  
  
## 備註  
 `_stat` 函式會取得 `path` 所指定之檔案或目錄的相關資訊，並將其儲存在 `buffer` 所指向的結構中。`_stat` 會根據目前使用中的多位元組字碼頁，自動將多位元組字元字串引數處理為適當且可辨識的多位元組字元序列。  
  
 `_wstat` 是寬字元版本的 `_stat`；`path` 的 `_wstat` 引數是寬字元字串。`_wstat` 與 `_stat` 的運作方式完全相同，不同之處在於 `_wstat` 不會處理多位元組字元字串。  
  
 這些函式的各種版本支援 32 位元或 64 位元時間類型，以及 32 位元或 64 位元檔案長度。 第一個數值後置字元 \(`32` 或 `64`\) 表示所使用的時間類型大小，第二個後置字元為 `i32` 或 `i64`，表示檔案大小是以 32 位元或 64 位元整數來表示。  
  
 `_stat` 相當於 `_stat64i32`, ，和 `struct``_stat` 包含 64 位元時間。 這是 true 除非 `_USE_32BIT_TIME_T` 定義在此情況下舊的行為是生效; `_stat` 使用 32 位元的時間和 `struct``_stat` 包含 32 位元時間。 對於 `_stati64` 也是如此。  
  
> [!NOTE]
>  `_wstat` 不適用於 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] 符號連結。 在這些情況下，`_wstat` 一律會回報檔案大小為 0。`_stat` 則適用於符號連結。  
  
 這個函式會驗證它的參數。 如果 `path` 或 `buffer` 為 `NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  
  
### \_stat 的時間類型和檔案長度類型版本  
  
|函式|是否已定義 \_USE\_32BIT\_TIME\_T？|時間類型|檔案長度類型|  
|--------|----------------------------------|----------|------------|  
|`_stat`, `_wstat`|未定義|64 位元|32 位元|  
|`_stat`, `_wstat`|已定義|32 位元|32 位元|  
|`_stat32`, `_wstat32`|不會受到巨集定義的影響|32 位元|32 位元|  
|`_stat64`, `_wstat64`|不會受到巨集定義的影響|64 位元|64 位元|  
|`_stati64`, `_wstati64`|未定義|64 位元|64 位元|  
|`_stati64`, `_wstati64`|已定義|32 位元|64 位元|  
|`_stat32i64`, `_wstat32i64`|不會受到巨集定義的影響|32 位元|64 位元|  
|`_stat64i32`, `_wstat64i32`|不會受到巨集定義的影響|64 位元|32 位元|  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tstat`|`_stat`|`_stat`|`_wstat`|  
|`_tstat64`|`_stat64`|`_stat64`|`_wstat64`|  
|`_tstati64`|`_stati64`|`_stati64`|`_wstati64`|  
|`_tstat32i64`|`_stat32i64`|`_stat32i64`|`_wstat32i64`|  
|`_tstat64i32`|`_stat64i32`|`_stat64i32`|`_wstat64i32`|  
  
 在 SYS\\STAT.H 中定義的 `_stat` 結構包含下列欄位。  
  
 `st_gid`  
 擁有檔案 \(UNIX 特定\) 之群組的數值識別碼。這個欄位在 Windows 系統上一律為零。 重新導向的檔案會歸類為 Windows 檔案。  
  
 `st_atime`  
 檔案的上次存取時間。 適用於 NTFS，但不適用 FAT 格式的磁碟機。  
  
 `st_ctime`  
 檔案的建立時間。 適用於 NTFS，但不適用 FAT 格式的磁碟機。  
  
 `st_dev`  
 內含檔案之磁碟的磁碟機數目 \(與 `st_rdev` 相同\)。  
  
 `st_ino`  
 檔案 \(UNIX 特定\) 的資訊節點數目 \(`inode`\)。 在 UNIX 檔案系統上，`inode` 會描述檔案日期和時間戳記、權限，以及內容。 當檔案彼此永久連結時，這些檔案會共用相同的 `inode`。`inode` 及之後的 `st_ino` 對 FAT、HPFS 或 NTFS 檔案系統沒有意義。  
  
 `st_mode`  
 檔案模式資訊的位元遮罩。 如果 `path` 指定目錄，會設定 `_S_IFDIR` 位元；如果 `path` 指定一般檔案或裝置，會設定 `_S_IFREG` 位元。 使用者讀取\/寫入位元會根據檔案的權限模式進行設定；使用者執行位元會根據副檔名進行設定。  
  
 `st_mtime`  
 檔案的上次修改時間。  
  
 `st_nlink`  
 在非 NTFS 檔案系統上一律為 1。  
  
 `st_rdev`  
 內含檔案之磁碟的磁碟機數目 \(與 `st_dev` 相同\)。  
  
 `st_size`  
 檔案大小 \(以位元組為單位\)；後置字元為 `i64` 的版本使用 64 位元整數**。**  
  
 `st_uid`  
 擁有檔案 \(UNIX 特定\) 之使用者的數值識別碼。 這個欄位在 Windows 系統上一律為零。 重新導向的檔案會歸類為 Windows 檔案。  
  
 如果 `path` 參考裝置，`_stat` 結構中的 `st_size`、各種時間欄位、`st_dev` 和 `st_rdev` 都沒有意義。 因為 STAT.H 使用在 TYPES.H 中定義的 [\_dev\_t](../../c-runtime-library/standard-types.md)，所以您必須在程式碼中的 STAT.H 之前包含 TYPES.H。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_stat`, `_stat32`, `_stat64`, `_stati64`, `_stat32i64`, `_stat64i32`|\<sys\/types.h\>，後面接著 \<sys\/stat.h\>|\<errno.h\>|  
|`_wstat`, `_wstat32`, `_wstat64`, `_wstati64`, `_wstat32i64`, `_wstat64i32`|\<sys\/types.h\>，後面接著 \<sys\/stat.h\> 或 \<wchar.h\>|\<errno.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
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
檔案大小：732 磁碟機：C: 修改時間：2002年 2 月 7 日星期四 14:39:36  
```  
  
## .NET Framework 對等用法  
  
-   [System::IO::File::GetAttributes](https://msdn.microsoft.com/en-us/library/system.io.file.getattributes.aspx)  
  
-   [System::IO::File::GetCreationTime](https://msdn.microsoft.com/en-us/library/system.io.file.getcreationtime.aspx)  
  
-   [System::IO::File::GetLastAccessTime](https://msdn.microsoft.com/en-us/library/system.io.file.getlastaccesstime.aspx)  
  
-   [System::IO::File::GetLastWriteTime](https://msdn.microsoft.com/en-us/library/system.io.file.getlastwritetime.aspx)  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [\_access、\_waccess](../../c-runtime-library/reference/access-waccess.md)   
 [\_fstat、\_fstat32、\_fstat64、\_fstati64、\_fstat32i64、\_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)