---
title: fseek、_fseeki64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- fseek
- _fseeki64
dev_langs:
- C++
helpviewer_keywords:
- _fseeki64 function
- fseeki64 function
- fseek function
- file pointers [C++], moving
- file pointers [C++]
- seek file pointers
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 266eb1589c97b177057e6a72874261c745acb475
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
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

*資料流*<br/>
**FILE** 結構的指標。

*offset*<br/>
從 *origin* 位移的位元組數目。

*origin*<br/>
初始位置。

## <a name="return-value"></a>傳回值

如果成功的話， **fseek**和 **_fseeki64**傳回 0。 否則，它會傳回非零值。 在無法搜尋的裝置上，傳回的值為未定義。 如果*資料流*為 null 指標，或如果*原點*不是其中一個允許的值如下所述， **fseek**和 **_fseeki64**叫用無效參數處理常式，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會將**errno**至**EINVAL**並傳回-1。

## <a name="remarks"></a>備註

**Fseek**和 **_fseeki64**函式的移動檔案指標 （如果有的話） 相關聯*資料流*至新位置*位移*從位元組*原點*。 資料流的下一個作業會在新位置進行。 在開啟以供更新的資料流中，下一項作業可能是讀取或寫入。 引數*原點*必須是下列常數 STDIO 中定義的其中一個。H:

|原始值|意義|
|-|-|
**SEEK_CUR**|檔案指標的目前位置。
**SEEK_END**|檔案結尾。
**SEEK_SET**|檔案開頭。

您可以使用**fseek**和 **_fseeki64**檔案中任何位置重新定位指標。 指標也可以放置在超過檔案結尾的位置。 **fseek**和 **_fseeki64**清除檔案結尾指標，並取消任何之前的效果[ungetc](ungetc-ungetwc.md)針對呼叫*資料流*。

檔案因為附加資料而開啟時，目前的檔案位置取決於最後一個 I/O 作業，而不是下一次寫入的位置。 如果開啟以供附加的檔案上尚未發生任何 I/O 作業，該檔案的位置是檔案的開頭。

在文字模式中開啟資料流的**fseek**和 **_fseeki64**有限使用，因為會造成歸位字元與換行字元傳回翻譯**fseek**和 **_fseeki64**來產生非預期的結果。 唯一**fseek**和 **_fseeki64**保證可以在文字模式開啟的資料流上運作的作業：

- 相對於任何原點值，位移為 0 的搜尋。

- 搜尋從位移的值與檔案的開頭傳回呼叫[ftell](ftell-ftelli64.md)時使用**fseek**或[_ftelli64](ftell-ftelli64.md)時使用 **_fseeki64**.

此外，在文字模式中，Ctrl+Z 會在輸入時被解譯成檔案結尾字元。 在檔案開啟為讀取/寫入， [fopen](fopen-wfopen.md)與所有相關的常式檢查是否有 CTRL + Z，檔案的結尾，然後盡可能移除它。 這是因為使用的組合**fseek**和[ftell](ftell-ftelli64.md)或 **_fseeki64**和[_ftelli64](ftell-ftelli64.md)，若要結束的檔案內移動CTRL + Z 可能會造成**fseek**或 **_fseeki64**檔案結尾附近產生不當行為。

當 CRT 開啟以位元順序標記 (BOM) 開頭的檔案時，檔案指標的位置在 BOM 之後 (也就是在檔案實際內容的開頭)。 如果您需要**fseek**檔案開頭，如果要使用[ftell](ftell-ftelli64.md)取得初始位置和**fseek**它，而不是位置 0。

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
