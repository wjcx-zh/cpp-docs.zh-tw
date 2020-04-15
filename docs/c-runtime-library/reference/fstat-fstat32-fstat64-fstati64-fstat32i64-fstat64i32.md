---
title: _fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32
ms.date: 4/2/2020
api_name:
- _fstat32
- _fstat64
- _fstati64
- _fstat
- _fstat64i32
- _fstat32i64
- _o__fstat32
- _o__fstat32i64
- _o__fstat64
- _o__fstat64i32
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 02d297fec2ada545a8b693abacfecc7981149dae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345675"
---
# <a name="_fstat-_fstat32-_fstat64-_fstati64-_fstat32i64-_fstat64i32"></a>_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32

取得開啟之檔案的相關資訊。

## <a name="syntax"></a>語法

```C
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

### <a name="parameters"></a>參數

*Fd*<br/>
已開啟之檔案的檔案描述項。

*緩衝區*<br/>
儲存結果的結構指標。

## <a name="return-value"></a>傳回值

如果取得檔案狀態資訊，則傳回 0。 返回值 -1 表示錯誤。 如果檔案描述符不合法或*緩衝區*為**NULL,** 則呼叫無效參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則**errno**設定為**EBADF**,如果檔描述符無效,則設置為**EINVAL(** 如果*緩衝區*為**NULL**)。

## <a name="remarks"></a>備註

**_fstat**函數獲取與*fd*關聯的打開檔的資訊,並將其存儲在*緩衝區*指向的結構中。 在 SYS_Stat.h 中定義的 **_stat**結構包含以下欄位。

|欄位|意義|
|-|-|
| **st_atime** | 最後存取檔案的時間。 |
| **st_ctime** | 建立檔案的時間。 |
| **st_dev** | 如果裝置 *,fd*;否則 0。 |
| **st_mode** | 檔案模式資訊的位元遮罩。 如果*fd*引用設備,則設置 **_S_IFCHR**位元。 如果*fd*引用普通檔,則設置 **_S_IFREG**位元。 讀取/寫入位元會根據檔案的權限模式設定。 **_S_IFCHR**和其他常量在 SYS_Stat.h 中定義。 |
| **st_mtime** | 檔案的上次修改時間。 |
| **st_nlink** | 在非 NTFS 檔案系統上一律為 1。 |
| **st_rdev** | 如果裝置 *,fd*;否則 0。 |
| **st_size** | 檔案大小，以位元組為單位。 |

如果*fd*引用設備,**則st_atime、st_ctime、st_mtime**和**st_size**欄位沒有意義。 **st_ctime** **st_mtime**

因為 Stat.h 使用在 Types.h 中定義的 [_dev_t](../../c-runtime-library/standard-types.md) 類型，所以您必須在程式碼中的 Stat.h 之前包含 Types.h。

**_fstat64 ()** 使用 **__stat64**結構,允許將檔案創建日期表達到 UTC 12 月 31 日 23:59:59;而其他函數僅表示 2038 年 1 月 18 日 23:59:59,UTC 的日期。 1970 年 1 月 1 日午夜是所有這些函式的日期範圍下限。

這些函式的變化支援 32 位元或 64 位元時間類型，以及 32 位元或 64 位元檔案長度。 第一個數字後綴 (**32**或**64**) 表示使用的時間類型的大小;第二個後綴是**i32**或**i64,** 指示檔大小是表示為 32 位元還是 64 位整數。

**_fstat**等效於 **_fstat64i32**,**結構****_stat**包含 64 位元時間。 除非定義了 **_USE_32BIT_TIME_T,** 否則這是事實,在這種情況下,舊行為有效;**_fstat**使用 32 位**時間,結構****_stat**包含 32 位元時間。 **_fstati64**也是如此。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="time-type-and-file-length-type-variations-of-_stat"></a>_stat 的時間類型和檔案長度類型版本

|函式|是否已定義 _USE_32BIT_TIME_T？|時間類型|檔案長度類型|
|---------------|------------------------------------|---------------|----------------------|
|**_fstat**|未定義|64 位元|32 位元|
|**_fstat**|已定義|32 位元|32 位元|
|**_fstat32**|不會受到巨集定義的影響|32 位元|32 位元|
|**_fstat64**|不會受到巨集定義的影響|64 位元|64 位元|
|**_fstati64**|未定義|64 位元|64 位元|
|**_fstati64**|已定義|32 位元|64 位元|
|**_fstat32i64**|不會受到巨集定義的影響|32 位元|64 位元|
|**_fstat64i32**|不會受到巨集定義的影響|64 位元|32 位元|

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**_fstat**|\<sys/stat.h> 和 \<sys/types.h>|
|**_fstat32**|\<sys/stat.h> 和 \<sys/types.h>|
|**_fstat64**|\<sys/stat.h> 和 \<sys/types.h>|
|**_fstati64**|\<sys/stat.h> 和 \<sys/types.h>|
|**_fstat32i64**|\<sys/stat.h> 和 \<sys/types.h>|
|**_fstat64i32**|\<sys/stat.h> 和 \<sys/types.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
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

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_access、_waccess](access-waccess.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_filelength、_filelengthi64](filelength-filelengthi64.md)<br/>
[_stat、_wstat 函式](stat-functions.md)<br/>
