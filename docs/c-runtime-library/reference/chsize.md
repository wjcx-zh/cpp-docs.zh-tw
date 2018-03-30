---
title: _chsize | Microsoft Docs
ms.custom: ''
ms.date: 03/29/2018
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _chsize
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _chsize
dev_langs:
- C++
helpviewer_keywords:
- size
- _chsize function
- size, changing file
- files [C++], changing size
- chsize function
ms.assetid: b3e881c5-7b27-4837-a3d4-c51591ab10ff
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cec2d058b356cbb7624ee6dd0bbecdfb55c64813
ms.sourcegitcommit: cdd4808dcb274bbb29618286df4d1d4acd35b9bc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2018
---
# <a name="chsize"></a>_chsize

變更檔案大小。 已有更安全的版本可用；請參閱 [_chsize_s](../../c-runtime-library/reference/chsize-s.md)。

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

_chsize` returns the value 0 if the file size is successfully changed. A return value of -1 indicates an error: `errno` is set to `EACCES` if the specified file is read-only or the specified file is locked against access, to `EBADF` if the descriptor is invalid, `ENOSPC` if no space is left on the device, or `EINVAL` if `大小 ' 小於零。

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

`_chsize` 函式會將與 `fd` 相關聯的檔案擴充或截斷至 `size` 所指定的長度。 檔案必須以允許寫入的模式開啟。 如果擴充檔案，則會附加 Null 字元 ('\0')。 如果檔案遭到截斷，則會遺失從縮短檔案結尾到檔案原始長度的所有資料。

這個函式會驗證它的參數。 如果 `size` 小於零，或 `fd` 是不正確的檔案描述元，則會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。

## <a name="requirements"></a>需求

|常式|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|`_chsize`|\<io.h>|\<errno.h>|

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
[_close](../../c-runtime-library/reference/close.md)<br/>
[_sopen、_wsopen](../../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_open、_wopen](../../c-runtime-library/reference/open-wopen.md)<br/>
