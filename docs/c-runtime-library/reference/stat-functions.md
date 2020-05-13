---
title: _stat、_stat32、_stat64、_stati64、_stat32i64、_stat64i32、_wstat、_wstat32、_wstat64、_wstati64、_wstat32i64、_wstat64i32
ms.date: 4/2/2020
api_name:
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
- _o__stat32
- _o__stat32i64
- _o__stat64
- _o__stat64i32
- _o__wstat32
- _o__wstat32i64
- _o__wstat64
- _o__wstat64i32
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 607a7aff3acf923e0dd62e0dc332283f66b436b1
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918314"
---
# <a name="_stat-_stat32-_stat64-_stati64-_stat32i64-_stat64i32-_wstat-_wstat32-_wstat64-_wstati64-_wstat32i64-_wstat64i32"></a>_stat、_stat32、_stat64、_stati64、_stat32i64、_stat64i32、_wstat、_wstat32、_wstat64、_wstati64、_wstat32i64、_wstat64i32

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

*緩衝區*<br/>
儲存結果的結構指標。

## <a name="return-value"></a>傳回值

上述每個函式會在取得檔案狀態資訊時傳回 0。 傳回值-1 表示發生錯誤，在此情況下， **errno**會設定為**ENOENT**，表示找不到檔案名或路徑。 **EINVAL**的傳回值表示不正確參數。在此情況下， **errno**也會設為**EINVAL** 。

如需此和其他傳回碼的詳細資訊，請參閱[_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。

如果檔案的日期戳記晚于1970年1月1日午夜，而在23:59:59 年12月 31 3000 日（UTC）之前，則可以表示，除非您使用 **_stat32**或 **_wstat32**，或已定義 **_USE_32BIT_TIME_T**，在這種情況下，日期只能表示到23:59:59 年1月 18 2038 日，utc 為止。

## <a name="remarks"></a>備註

**_Stat**函式會取得*path*所指定之檔案或目錄的相關資訊，並將它儲存在*buffer*所指向的結構中。 **_stat**會根據目前使用中的多位元組字碼頁，自動將多位元組字元字串引數處理為適當的，並辨識多位元組字元序列。

**_wstat**是寬字元版本的 **_stat**;**_wstat**的*path*引數是寬字元字串。 **_wstat**和 **_stat**的行為相同，不同之處在于 **_wstat**不會處理多位元組字元字串。

這些函式的各種版本支援 32 位元或 64 位元時間類型，以及 32 位元或 64 位元檔案長度。 第一個數位尾碼（**32**或**64**）表示所使用的時間類型大小;第二個尾碼為**i32**或**i64**，指出檔案大小是否以32位或64位整數表示。

**_stat**相當於 **_stat64i32**，而**struct** **_stat**包含64位時間。 除非已定義 **_USE_32BIT_TIME_T** （在此情況下，舊的行為會生效），否則為 true。**_stat**使用32位時間，而**結構** **_stat**包含32位時間。 **_Stati64**的情況也是如此。

> [!NOTE]
> **_wstat**無法用於 Windows Vista 符號連結。 在這些情況下， **_wstat**一律會報告檔案大小為0。 **_stat**可搭配符號連結正常運作。

這個函式會驗證它的參數。 如果*路徑*或*緩衝區*為**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="time-type-and-file-length-type-variations-of-_stat"></a>_stat 的時間類型和檔案長度類型版本

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

**_Stat**結構，定義于 SYS\STAT。H，包含下欄欄位。

|欄位||
|-|-|
| **st_gid** | 擁有檔案 (UNIX 特定) 之群組的數值識別碼。這個欄位在 Windows 系統上一律為零。 重新導向的檔案會歸類為 Windows 檔案。 |
| **st_atime** | 檔案的上次存取時間。 適用於 NTFS，但不適用 FAT 格式的磁碟機。 |
| **st_ctime** | 檔案的建立時間。 適用於 NTFS，但不適用 FAT 格式的磁碟機。 |
| **st_dev** | 包含檔案的磁片磁碟機號（與**st_rdev**相同）。 |
| **st_ino** | 檔案（UNIX 特定）的資訊節點數目（ **inode**）。 在 UNIX 檔案系統上， **inode**會描述檔案日期和時間戳記、許可權和內容。 當檔案永久連結到另一個檔案時，它們會共用相同的**inode**。 因此， **inode**（因此**ST_INO**）在 FAT、HPFS 或 NTFS 檔案系統中沒有意義。 |
| **st_mode** | 檔案模式資訊的位元遮罩。 如果*path*指定目錄，則會設定 **_S_IFDIR**位;如果*path*指定一般檔案或裝置，則會設定 **_S_IFREG**位。 使用者讀取/寫入位元會根據檔案的權限模式進行設定；使用者執行位元會根據副檔名進行設定。 |
| **st_mtime** | 檔案的上次修改時間。 |
| **st_nlink** | 在非 NTFS 檔案系統上一律為 1。 |
| **st_rdev** | 包含檔案的磁片磁碟機號（與**st_dev**相同）。 |
| **st_size** | 檔案大小（以位元組為單位）;具有**i64**後置詞之變數的64位整數。 |
| **st_uid** | 擁有檔案 (UNIX 特定) 之使用者的數值識別碼。 這個欄位在 Windows 系統上一律為零。 重新導向的檔案會歸類為 Windows 檔案。 |

如果*path*參照裝置， **_stat**結構中的**st_size**、各種時間欄位、 **st_dev**和**st_rdev**欄位就沒有意義。 因為 STAT.H 使用在 TYPES.H 中定義的 [_dev_t](../../c-runtime-library/standard-types.md) 類型，所以您必須在程式碼中的 STAT.H 之前包含 TYPES.H。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|----------------------|
|**_stat**、 **_stat32**、 **_stat64**、 **_stati64**、 **_stat32i64**、 **_stat64i32**|\<sys/types.h>，後面接著 \<sys/stat.h>|\<errno.h>|
|**_wstat**、 **_wstat32**、 **_wstat64**、 **_wstati64**、 **_wstat32i64**、 **_wstat64i32**|\<sys/types.h>，後面接著 \<sys/stat.h> 或 \<wchar.h>|\<errno.h>|

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
