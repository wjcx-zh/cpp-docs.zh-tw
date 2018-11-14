---
title: _stat、_stat32、_stat64、_stati64、_stat32i64、_stat64i32、_wstat、_wstat32、_wstat64、_wstati64、_wstat32i64、_wstat64i32
ms.date: 11/04/2016
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
ms.openlocfilehash: d9272cd4596a54a38e1ba21ac92b038c2da0d207
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51331200"
---
# <a name="stat-stat32-stat64-stati64-stat32i64-stat64i32-wstat-wstat32-wstat64-wstati64-wstat32i64-wstat64i32"></a>_stat、_stat32、_stat64、_stati64、_stat32i64、_stat64i32、_wstat、_wstat32、_wstat64、_wstati64、_wstat32i64、_wstat64i32

取得檔案的狀態資訊。

## <a name="syntax"></a>語法

```C
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

### <a name="parameters"></a>參數

*path*<br/>
包含現有檔案或目錄路徑的字串指標。

*buffer*<br/>
儲存結果的結構指標。

## <a name="return-value"></a>傳回值

上述每個函式會在取得檔案狀態資訊時傳回 0。 傳回值為-1 表示發生錯誤時，在此情況下**errno**設為**ENOENT**，指出，檔案名稱或路徑找不到。 傳回值**EINVAL**表示無效的參數;**errno**也會設定為**EINVAL**在此情況下。

如需這個及其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。

如果是 1970 年 1 月 1 日午夜之前 23:59:59，3000 年 12 月 31 日 UTC，除非您使用，就可以表示檔案的日期戳記 **_stat32**或 **_wstat32**，或者已定義 **_USE_32BIT_TIME_T**，在此情況下代表的日期，只會保存 23:59:59 2038 年 1 月 18 日 UTC。

## <a name="remarks"></a>備註

**_Stat**函式會取得檔案或目錄所指定的資訊*路徑*並將它儲存在結構中所指*緩衝區*。 **_stat**自動多位元組字元字串引數處理為適當，辨識多位元組字元序列，根據目前使用中的多位元組字碼頁。

**_wstat**是寬字元版本的 **_stat**;*路徑*引數 **_wstat**是寬字元字串。 **_wstat**並 **_stat**運作方式完全相同，不同之處在於 **_wstat**不會處理多位元組字元字串。

這些函式的各種版本支援 32 位元或 64 位元時間類型，以及 32 位元或 64 位元檔案長度。 第一個數值尾碼 (**32**或**64**) 表示時間的大小類型使用，第二個尾碼為**i32**或是**i64**，表示檔案大小以 32 位元或 64 位元的整數。

**_stat**相當於 **_stat64i32**，以及**結構** **_stat**包含 64 位元時間。 這適用於除非 **_USE_32BIT_TIME_T**定義，在此情況下會採用舊版行為生效;**_stat**使用 32 位元時間，以及**結構** **_stat**包含 32 位元時間。 這也適用於 **_stati64**。

> [!NOTE]
> **_wstat**不適用於 Windows Vista 的符號連結。 在這些情況下， **_wstat**一律會回報檔案大小為 0。 **_stat**則適用於符號連結。

這個函式會驗證它的參數。 如果有任一*路徑*或是*緩衝區*是**NULL**，無效參數處理常式會叫用，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。

### <a name="time-type-and-file-length-type-variations-of-stat"></a>_stat 的時間類型和檔案長度類型版本

|函式|是否已定義 _USE_32BIT_TIME_T？|時間類型|檔案長度類型|
|---------------|------------------------------------|---------------|----------------------|
|**_stat**， **_wstat**|未定義|64 位元|32 位元|
|**_stat**， **_wstat**|已定義|32 位元|32 位元|
|**_stat32**， **_wstat32**|不會受到巨集定義的影響|32 位元|32 位元|
|**_stat64**， **_wstat64**|不會受到巨集定義的影響|64 位元|64 位元|
|**_stati64**， **_wstati64**|未定義|64 位元|64 位元|
|**_stati64**， **_wstati64**|已定義|32 位元|64 位元|
|**_stat32i64**， **_wstat32i64**|不會受到巨集定義的影響|32 位元|64 位元|
|**_stat64i32**， **_wstat64i32**|不會受到巨集定義的影響|64 位元|32 位元|

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstat**|**_stat**|**_stat**|**_wstat**|
|**_tstat64**|**_stat64**|**_stat64**|**_wstat64**|
|**_tstati64**|**_stati64**|**_stati64**|**_wstati64**|
|**_tstat32i64**|**_stat32i64**|**_stat32i64**|**_wstat32i64**|
|**_tstat64i32**|**_stat64i32**|**_stat64i32**|**_wstat64i32**|

**_Stat** SYS\STAT 中定義的結構。H，包含下列欄位。

|欄位||
|-|-|
| **st_gid** | 擁有檔案 (UNIX 特定) 之群組的數值識別碼。這個欄位在 Windows 系統上一律為零。 重新導向的檔案會歸類為 Windows 檔案。 |
| **st_atime** | 檔案的上次存取時間。 適用於 NTFS，但不適用 FAT 格式的磁碟機。 |
| **st_ctime** | 檔案的建立時間。 適用於 NTFS，但不適用 FAT 格式的磁碟機。 |
| **st_dev** | 磁碟機的包含檔的磁碟數目 (與相同**st_rdev**)。 |
| **st_ino** | 資訊的節點數目 ( **inode**) 檔案 （UNIX 特定）。 在 UNIX 檔案系統**inode**描述檔案日期和時間戳記、 權限，以及內容。 當檔案永久連結至另一部，它們會共用相同**inode**。 **Inode**，因此**st_ino**，FAT、 HPFS 或 NTFS 檔案系統中沒有任何意義。 |
| **st_mode** | 檔案模式資訊的位元遮罩。 **_S_IFDIR**如果設定位元*路徑*指定的目錄，而 **_S_IFREG**位元設定如果*路徑*指定一般檔案或裝置。 使用者讀取/寫入位元會根據檔案的權限模式進行設定；使用者執行位元會根據副檔名進行設定。 |
| **st_mtime** | 檔案的上次修改時間。 |
| **st_nlink** | 在非 NTFS 檔案系統上一律為 1。 |
| **st_rdev** | 磁碟機的包含檔的磁碟數目 (與相同**st_dev**)。 |
| **st_size** | 以位元組為單位; 檔的大小版本使用 64 位元整數**i64**後置詞。 |
| **st_uid** | 擁有檔案 (UNIX 特定) 之使用者的數值識別碼。 這個欄位在 Windows 系統上一律為零。 重新導向的檔案會歸類為 Windows 檔案。 |

如果*路徑*指的是裝置， **st_size**、 各種時間欄位、 **st_dev**，以及**st_rdev**中的欄位 **_stat**結構便沒有意義。 因為 STAT.H 使用在 TYPES.H 中定義的 [_dev_t](../../c-runtime-library/standard-types.md) ，所以您必須在程式碼中的 STAT.H 之前包含 TYPES.H。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|----------------------|
|**_stat**， **_stat32**， **_stat64**， **_stati64**， **_stat32i64**， **_stat64i32**|\<sys/types.h>，後面接著 \<sys/stat.h>|\<errno.h>|
|**_wstat**， **_wstat32**， **_wstat64**， **_wstati64**， **_wstat32i64**， **_wstat64i32**|\<sys/types.h>，後面接著 \<sys/stat.h> 或 \<wchar.h>|\<errno.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
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

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_access、_waccess](access-waccess.md)<br/>
[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_setmbcp](setmbcp.md)<br/>
