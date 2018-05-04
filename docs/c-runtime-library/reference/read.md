---
title: _read | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _read
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
- _read
dev_langs:
- C++
helpviewer_keywords:
- data [CRT]
- _read function
- read function
- data [C++], reading
- reading data [C++]
- files [C++], reading
ms.assetid: 2ce9c433-57ad-47fe-9ac1-4a7d4c883d30
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c67ce8ac0e754bf3003b23c56cd1d3f428be903
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="read"></a>_read

從檔案讀取資料。

## <a name="syntax"></a>語法

```C
int _read(
   int fd,
   void *buffer,
   unsigned int count
);
```

### <a name="parameters"></a>參數

*fd*<br/>
參照已開啟之檔案的檔案描述元。

*buffer*<br/>
資料的儲存位置。

*count*<br/>
最大位元組數。

## <a name="return-value"></a>傳回值

**閱讀**傳回讀取位元組數，這可能會小於比*計數*如果少於*計數*位元組保留在檔案中，或如果在文字模式中開啟檔案，在此情況下每個歸位字元換行字元組 '\r\n' 會取代單一換行字元 '\n'。 在傳回值中只會計算單一換行字元。 這種取代不會影響檔案指標。

如果函式嘗試讀取檔案的結尾，則會傳回 0。 如果*fd*不是正確，檔案不是開啟可供讀取，或檔案鎖定、 無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，函式會傳回-1 以及設定執行**errno**至**EBADF**。

如果 *buffer* 為 **NULL**，則會叫用無效的參數處理常式。 如果允許繼續執行，此函數會傳回-1 和**errno**設**EINVAL**。

如需此傳回碼與其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**閱讀**函式會讀取最多*計數*位元組*緩衝區*與相關聯的檔案從*fd*。 讀取作業會從與指定檔案相關之檔案指標的目前位置開始。 讀取作業之後，檔案指標會指向下一個未讀取的字元。

如果在文字模式中開啟檔案，在讀取時就會終止**閱讀**遇到 CTRL + Z 字元視為檔案結尾指標。 使用 [_lseek](lseek-lseeki64.md) 可清除檔案結尾指標。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_read**|\<io.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_read.c
/* This program opens a file named crt_read.txt
* and tries to read 60,000 bytes from
* that file using _read. It then displays the
* actual number of bytes read.
*/

#include <fcntl.h>      /* Needed only for _O_RDWR definition */
#include <io.h>
#include <stdlib.h>
#include <stdio.h>
#include <share.h>

char buffer[60000];

int main( void )
{
   int fh;
   unsigned int nbytes = 60000, bytesread;

   /* Open file for input: */
   if( _sopen_s( &fh, "crt_read.txt", _O_RDONLY, _SH_DENYNO, 0 ) )
   {
      perror( "open failed on input file" );
      exit( 1 );
   }

   /* Read in input: */
   if( ( bytesread = _read( fh, buffer, nbytes ) ) <= 0 )
      perror( "Problem reading file" );
   else
      printf( "Read %u bytes from file\n", bytesread );

   _close( fh );
}
```

### <a name="input-crtreadtxt"></a>輸入︰crt_read.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>輸出

```Output
Read 19 bytes from file
```

## <a name="see-also"></a>另請參閱

[低層級 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[fread](fread.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_write](write.md)<br/>
