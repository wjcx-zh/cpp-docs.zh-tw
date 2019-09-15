---
title: _chsize
ms.date: 03/29/2018
api_name:
- _chsize
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _chsize
helpviewer_keywords:
- size
- _chsize function
- size, changing file
- files [C++], changing size
- chsize function
ms.assetid: b3e881c5-7b27-4837-a3d4-c51591ab10ff
ms.openlocfilehash: 7fe07b2261396be491b833ff52186024edd0b919
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942969"
---
# <a name="_chsize"></a>_chsize

變更檔案大小。 已有更安全的版本可用；請參閱 [_chsize_s](chsize-s.md)。

## <a name="syntax"></a>語法

```C
int _chsize(
   int fd,
   long size
);
```

### <a name="parameters"></a>參數

*fd*<br/>
參考已開啟檔案的檔案描述項。

*size*<br/>
檔案的新長度 (位元組)。

## <a name="return-value"></a>傳回值

如果成功變更檔案大小， **_chsize**會傳回0值。 傳回值-1 表示錯誤：如果指定的檔案是唯讀的，或指定的檔案已鎖定而無法存取，則會將**errno**設定為**EACCES** ; 如果描述元無效，則為**EBADF** ; 如果裝置上沒有空間，則為**ENOSPC** ，或如果*大小*小於零，則為**EINVAL** 。

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Chsize**函式會將與*fd*相關聯的檔案擴充或截斷到*size*所指定的長度。 檔案必須以允許寫入的模式開啟。 如果擴充檔案，則會附加 Null 字元 ('\0')。 如果檔案遭到截斷，則會遺失從縮短檔案結尾到檔案原始長度的所有資料。

這個函式會驗證它的參數。 如果*size*小於零或*fd*是不正確的檔案描述項，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_chsize**|\<io.h>|\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_chsize.c
// This program uses _filelength to report the size
// of a file before and after modifying it with _chsize.

#include <io.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <stdio.h>
#include <share.h>

int main( void )
{
   int fh, result;
   unsigned int nbytes = BUFSIZ;

   // Open a file
   if( _sopen_s( &fh, "data", _O_RDWR | _O_CREAT, _SH_DENYNO,
                 _S_IREAD | _S_IWRITE ) == 0 )
   {
      printf( "File length before: %ld\n", _filelength( fh ) );
      if( ( result = _chsize( fh, 329678 ) ) == 0 )
         printf( "Size successfully changed\n" );
      else
         printf( "Problem in changing the size\n" );
      printf( "File length after:  %ld\n", _filelength( fh ) );
      _close( fh );
   }
}
```

```Output
File length before: 0
Size successfully changed
File length after:  329678
```

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_sopen、_wsopen](sopen-wsopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
