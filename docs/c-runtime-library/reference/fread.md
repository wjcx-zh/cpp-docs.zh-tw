---
title: fread
ms.date: 11/04/2016
apiname:
- fread
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
- fread
helpviewer_keywords:
- reading data [C++], from input streams
- fread function
- data [C++], reading from input stream
- streams [C++], reading data from
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
ms.openlocfilehash: d3516dc67047064b9293b1bb289888596736ed47
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468831"
---
# <a name="fread"></a>fread

從資料流讀取資料。

## <a name="syntax"></a>語法

```C
size_t fread(
   void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>參數

*buffer*<br/>
資料的儲存位置。

*size*<br/>
項目大小 (位元組)。

*count*<br/>
要讀取項目的最大數量。

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

**fread**傳回實際讀取的完整項目數，可能會小於*計數*發生錯誤，或如果到達之前遇到檔案結尾，則*計數*。 使用**feof**或是**ferror**函式來區分讀取的錯誤與檔案結尾條件。 如果*大小*或是*計數*為 0， **fread**傳回 0，而且緩衝區內容未變更。 如果*資料流*或是*緩衝區*為 null 指標， **fread**叫用無效參數處理常式，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**要**EINVAL**且會傳回 0。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Fread**函式會讀取多達*計數*的項目*大小*從輸入位元組*串流*並將它們儲存在*緩衝區*. 與相關聯的檔案指標*資料流*（如果有的話） 會增加實際讀取的位元組數目。 如果指定的資料流以文字模式開啟，則歸位字元復位換行組，將取代為單一換行字元。 這種取代不會影響檔案指標或傳回值。 發生錯誤時，無法確定檔案指標位置。 無法判斷部分讀取項目的值。

此函式會鎖定其他執行緒。 如果您需要非鎖定版本時，使用 **_fread_nolock**。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**fread**|\<stdio.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_fread.c
// This program opens a file named FREAD.OUT and
// writes 25 characters to the file. It then tries to open
// FREAD.OUT and read in 25 characters. If the attempt succeeds,
// the program displays the number of actual items read.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char list[30];
   int  i, numread, numwritten;

   // Open file in text mode:
   if( fopen_s( &stream, "fread.out", "w+t" ) == 0 )
   {
      for ( i = 0; i < 25; i++ )
         list[i] = (char)('z' - i);
      // Write 25 characters to stream
      numwritten = fwrite( list, sizeof( char ), 25, stream );
      printf( "Wrote %d items\n", numwritten );
      fclose( stream );

   }
   else
      printf( "Problem opening the file\n" );

   if( fopen_s( &stream, "fread.out", "r+t" ) == 0 )
   {
      // Attempt to read in 25 characters
      numread = fread( list, sizeof( char ), 25, stream );
      printf( "Number of items read = %d\n", numread );
      printf( "Contents of buffer = %.25s\n", list );
      fclose( stream );
   }
   else
      printf( "File could not be opened\n" );
}
```

```Output
Wrote 25 items
Number of items read = 25
Contents of buffer = zyxwvutsrqponmlkjihgfedcb
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
