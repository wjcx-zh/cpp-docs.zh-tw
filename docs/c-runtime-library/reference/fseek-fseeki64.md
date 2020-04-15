---
title: fseek、_fseeki64
ms.date: 4/2/2020
api_name:
- _fseeki64
- fseek
- _o__fseeki64
- _o_fseek
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
ms.openlocfilehash: e8f6021a0b770f6b435653c190d5968f9ac50a57
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345759"
---
# <a name="fseek-_fseeki64"></a>fseek、_fseeki64

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

*資料流*<br/>
**FILE** 結構的指標。

*位移*<br/>
從 *origin* 位移的位元組數目。

*起源*<br/>
初始位置。

## <a name="return-value"></a>傳回值

如果成功 **,fseek**和 **_fseeki64**返回 0。 否則，它會傳回非零值。 在無法搜尋的裝置上，傳回的值未定義。 如果*流*是空指標,或者如果*原點*不是下面描述的允許值之一 **,fseek**和 **_fseeki64**調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,這些函數將**errno**設置為**EINVAL**並返回 -1。

## <a name="remarks"></a>備註

**fseek**和 **_fseeki64**函數將與*流*關聯的檔指標(如果有)移至從*原點**偏移*位元組的新位置。 資料流的下一個作業會在新位置進行。 在開啟以供更新的資料流中，下一項作業可能是讀取或寫入。 參數*原點*必須是 STDIO 中定義的以下常量之一。H:

|原點值|意義|
|-|-|
| **SEEK_CUR** | 檔案指標的目前位置。 |
| **SEEK_END** | 檔案結尾。 |
| **SEEK_SET** | 檔案開頭。 |

您可以使用**fseek**和 **_fseeki64**重新定位檔案中的任意位置的指標。 指標也可以放置在超過檔案結尾的位置。 **fseek**和 **_fseeki64**清除檔結尾指示器,並否定任何以前的[不加點](ungetc-ungetwc.md)調用對*流*的影響。

檔案因為附加資料而開啟時，目前的檔案位置取決於最後一個 I/O 作業，而不是下一次寫入的位置。 如果開啟以供附加的檔案上尚未發生任何 I/O 作業，該檔案的位置是檔案的開頭。

對於在文本模式下打開的流 **,fseek**和 **_fseeki64**的使用有限,因為回饋線轉換可能會導致**fseek**和 **_fseeki64**產生意外的結果。 保證在文字模式下開啟的流上工作的唯**一 fseek**和 **_fseeki64**操作是:

- 相對於任何原點值，位移為 0 的搜尋。

- 使用**fseek**或_ftelli64時使用 _fseeki64 **fseek**或[_ftelli64](ftell-ftelli64.md)時,從檔的開頭查找從調用[ftell](ftell-ftelli64.md)返回的偏移值。

此外，在文字模式中，Ctrl+Z 會在輸入時被解譯成檔案結尾字元。 在打開用於讀取/寫入的檔中[,fopen](fopen-wfopen.md)和所有相關例程檢查檔末尾的 CTRL_Z,並盡可能將其刪除。 這樣做是因為使用**fseek**和[ftell](ftell-ftelli64.md)或 **_fseeki64**和[_ftelli64](ftell-ftelli64.md)的組合,在以 CTRL_Z 結尾的檔內移動可能會導致**fseek**或 **_fseeki64**在檔末尾附近行為不當。

當 CRT 開啟以位元順序標記 (BOM) 開頭的檔案時，檔案指標的位置在 BOM 之後 (也就是在檔案實際內容的開頭)。 如果必須**fseek**到檔的開頭,請使用[ftell](ftell-ftelli64.md)獲取初始位置和**fseek**到它,而不是定位 0。

此函式於執行期間鎖定其他執行緒，因此為安全執行緒。 如需非鎖定版本，請參閱 [_fseek_nolock、_fseeki64_nolock](fseek-nolock-fseeki64-nolock.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**fseek**|\<stdio.h>|
|**_fseeki64**|\<stdio.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
[倒](rewind.md)<br/>
