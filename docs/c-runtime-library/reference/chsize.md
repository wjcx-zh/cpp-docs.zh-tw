---
title: _chsize
ms.date: 4/2/2020
api_name:
- _chsize
- _o__chsize
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: bb2d72e40796a1dd2253361626042486490c77d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350060"
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

*Fd*<br/>
參照已開啟之檔案的檔案描述元。

*大小*<br/>
檔案的新長度 (位元組)。

## <a name="return-value"></a>傳回值

如果檔大小已成功更改 **,_chsize**返回值 0。 傳回值 -1 表示錯誤:如果指定的檔為唯讀檔或指定檔被鎖定反對存取,則錯誤設置為 EACCES;如果描述符**無效,則**將**errno**設置為 EACCES;如果描述符無效,則將 errno 設置為 EACCES;如果設備上沒有空間,則將 errno 設置為**EACCES;** 如果*大小*小於零,則**EINVAL 設定為 EINVAL。** **EBADF**

有關這些代碼和其他返回代碼的詳細資訊[,請參閱_doserrno、errno、_sys_errlist和_sys_nerr。](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>備註

**_chsize**函數將與*fd*關聯的檔擴展或截截到*大小*指定的長度。 檔案必須以允許寫入的模式開啟。 如果擴充檔案，則會附加 Null 字元 ('\0')。 如果檔案遭到截斷，則會遺失從縮短檔案結尾到檔案原始長度的所有資料。

這個函式會驗證它的參數。 如果*大小*小於零或*fd*是一個壞的檔描述符,則調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_chsize**|\<io.h>|\<errno.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

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
