---
title: _read
ms.date: 02/13/2019
api_name:
- _read
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
- _read
helpviewer_keywords:
- data [CRT]
- _read function
- read function
- data [C++], reading
- reading data [C++]
- files [C++], reading
ms.assetid: 2ce9c433-57ad-47fe-9ac1-4a7d4c883d30
ms.openlocfilehash: 32238923aeef14230f68def15e27c676753faf61
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949540"
---
# <a name="_read"></a>_read

從檔案讀取資料。

## <a name="syntax"></a>語法

```C
int _read(
   int const fd,
   void * const buffer,
   unsigned const buffer_size
);
```

### <a name="parameters"></a>參數

*fd*<br/>
參照已開啟之檔案的檔案描述元。

*buffer*<br/>
資料的儲存位置。

*buffer_size*<br/>
要讀取的最大位元組數。

## <a name="return-value"></a>傳回值

**_read**會傳回讀取的位元組數目，如果檔案中剩餘少於*buffer_size*個位元組，或者檔案是以文字模式開啟，則可能小於*buffer_size* 。 在文字模式中, 每個換行`\r\n`字元摘要組都會取代為單一換行字元。 `\n` 只有單行換行字元會在傳回值中計算。 這種取代不會影響檔案指標。

如果函式嘗試讀取檔案的結尾，則會傳回 0。 如果*fd*無效, 檔案不會開啟以供讀取, 或檔案已鎖定, 則會叫用不正確參數處理常式, 如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行, 此函式會傳回-1, 並將**errno**設定為**EBADF**。

如果*buffer*為**Null**，或*buffer_size*  >  **INT_MAX**，則會叫用不正確參數處理常式。 如果允許繼續執行, 此函式會傳回-1, 而**errno**會設定為**EINVAL**。

如需此函式與其他傳回碼的詳細資訊，請參閱 [_doserrno, errno、_sys_errlist 及 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Read**函數會從與*fd*相關聯的檔案中，讀取最多*buffer_size*個位元組到*緩衝區*。 讀取作業會從與指定檔案相關之檔案指標的目前位置開始。 讀取作業之後，檔案指標會指向下一個未讀取的字元。

如果檔案是在文字模式中開啟，當 **_read**遇到 CTRL + Z 字元時，讀取就會終止，這會被視為檔案結尾指標。 使用 [_lseek](lseek-lseeki64.md) 可清除檔案結尾指標。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
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
   int fh, bytesread;
   unsigned int nbytes = 60000;

   /* Open file for input: */
   if ( _sopen_s( &fh, "crt_read.txt", _O_RDONLY, _SH_DENYNO, 0 ))
   {
      perror( "open failed on input file" );
      exit( 1 );
   }

   /* Read in input: */
   if (( bytesread = _read( fh, buffer, nbytes )) <= 0 )
      perror( "Problem reading file" );
   else
      printf( "Read %u bytes from file\n", bytesread );

   _close( fh );
}
```

### <a name="input-crt_readtxt"></a>輸入︰crt_read.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
Read 19 bytes from file
```

## <a name="see-also"></a>另請參閱

[低層級 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[fread](fread.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_write](write.md)<br/>
