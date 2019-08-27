---
title: fseek、_fseeki64
ms.date: 11/04/2016
apiname:
- _fseeki64
- fseek
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
- fseek
- _fseeki64
helpviewer_keywords:
- _fseeki64 function
- fseeki64 function
- fseek function
- file pointers [C++], moving
- file pointers [C++]
- seek file pointers
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
ms.openlocfilehash: 4cfb4bcea4a110cf8a9c9db664c42d6603328cf0
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376093"
---
# <a name="fseek-fseeki64"></a>fseek、_fseeki64

將檔案指標移至指定的位置。

## <a name="syntax"></a>語法

```C
int fseek(
   FILE *stream,
   long offset,
   int origin
);
int _fseeki64(
   FILE *stream,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>參數

*stream*<br/>
**FILE** 結構的指標。

*offset*<br/>
從 *origin* 位移的位元組數目。

*origin*<br/>
初始位置。

## <a name="return-value"></a>傳回值

如果成功, **fseek**和 **_fseeki64**就會傳回0。 否則，它會傳回非零值。 在無法搜尋的裝置上，傳回的值為未定義。 如果*stream*是 null 指標, 或如果*來源*不是以下所述的允許值之一, 則**fseek**和 **_fseeki64**會叫用不正確參數處理常式, 如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行, 這些函式會將**errno**設定為**EINVAL** , 並傳回-1。

## <a name="remarks"></a>備註

**Fseek**和 **_fseeki64**函式會將與*資料流程*相關聯的檔案指標 (如果有的話) 移至從*來源* *位移*位元組的新位置。 資料流的下一個作業會在新位置進行。 在開啟以供更新的資料流中，下一項作業可能是讀取或寫入。 引數*原點*必須是下列其中一個常數 (定義于 stdio.h 中)。H

|原始值|意義|
|-|-|
| **SEEK_CUR** | 檔案指標的目前位置。 |
| **SEEK_END** | 檔案結尾。 |
| **SEEK_SET** | 檔案開頭。 |

您可以使用**fseek**和 **_fseeki64** , 將指標重新放置在檔案中的任何位置。 指標也可以放置在超過檔案結尾的位置。 **fseek**和 **_fseeki64**會清除檔案結尾指標, 並否定任何先前[ungetc](ungetc-ungetwc.md)呼叫對*資料流程*的影響。

檔案因為附加資料而開啟時，目前的檔案位置取決於最後一個 I/O 作業，而不是下一次寫入的位置。 如果開啟以供附加的檔案上尚未發生任何 I/O 作業，該檔案的位置是檔案的開頭。

針對在文字模式中開啟的資料流程, **fseek**和 **_fseeki64**的用途有限, 因為換行字元摘要翻譯可能會導致**fseek**和 **_fseeki64**產生非預期的結果。 唯一保證在以文字模式開啟的資料流程上運作的**fseek**和 **_fseeki64**作業如下:

- 相對於任何原點值，位移為 0 的搜尋。

- 使用 **_fseeki64**時, 使用**fseek**或[_ftelli64](ftell-ftelli64.md)時, 從檔案的開頭開始搜尋, 其中包含從呼叫[ftell](ftell-ftelli64.md)所傳回的位移值。

此外，在文字模式中，Ctrl+Z 會在輸入時被解譯成檔案結尾字元。 在為了讀取/寫入而開啟的檔案中, [fopen](fopen-wfopen.md)和所有相關的常式會檢查檔案結尾是否有 CTRL + Z, 並盡可能加以移除。 這是因為使用**fseek**和[ftell](ftell-ftelli64.md)或 **_fseeki64**和[_ftelli64](ftell-ftelli64.md)的組合, 在以 CTRL + Z 結束的檔案內移動, 可能會導致**fseek**或 **_fseeki64**在接近結尾的地方出現不正確的行為文字檔.

當 CRT 開啟以位元順序標記 (BOM) 開頭的檔案時，檔案指標的位置在 BOM 之後 (也就是在檔案實際內容的開頭)。 如果您必須**fseek**至檔案的開頭, 請使用[ftell](ftell-ftelli64.md)來取得初始位置並**fseek**至其位置, 而不是定位0。

此函式於執行期間鎖定其他執行緒，因此為安全執行緒。 如需非鎖定版本，請參閱 [_fseek_nolock、_fseeki64_nolock](fseek-nolock-fseeki64-nolock.md)。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**fseek**|\<stdio.h>|
|**_fseeki64**|\<stdio.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_fseek.c
// This program opens the file FSEEK.OUT and
// moves the pointer to the file's beginning.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char line[81];
   int  result;

   if ( fopen_s( &stream, "fseek.out", "w+" ) != 0 )
   {
      printf( "The file fseek.out was not opened\n" );
      return -1;
   }
   fprintf( stream, "The fseek begins here: "
                    "This is the file 'fseek.out'.\n" );
   result = fseek( stream, 23L, SEEK_SET);
   if( result )
      perror( "Fseek failed" );
   else
   {
      printf( "File pointer is set to middle of first line.\n" );
      fgets( line, 80, stream );
      printf( "%s", line );
    }
   fclose( stream );
}
```

```Output
File pointer is set to middle of first line.
This is the file 'fseek.out'.
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[ftell、_ftelli64](ftell-ftelli64.md)<br/>
[_lseek、_lseeki64](lseek-lseeki64.md)<br/>
[rewind](rewind.md)<br/>
