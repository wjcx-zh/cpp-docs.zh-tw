---
title: fread
ms.date: 11/28/2018
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
ms.openlocfilehash: 7248eb08409b50d855dbb70c7638a856302b345b
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849967"
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

*stream*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

**fread**傳回實際讀取的完整項目數，可能會小於*計數*發生錯誤，或如果到達之前遇到檔案結尾，則*計數*。 使用**feof**或是**ferror**函式來區分讀取的錯誤與檔案結尾條件。 如果*大小*或是*計數*為 0， **fread**傳回 0，而且緩衝區內容未變更。 如果*資料流*或是*緩衝區*為 null 指標， **fread**叫用無效參數處理常式，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**要**EINVAL**且會傳回 0。

請參閱[ \_doserrno，errno， \_sys\_errlist，並\_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)如需有關這些錯誤碼。

## <a name="remarks"></a>備註

**Fread**函式會讀取多達*計數*的項目*大小*從輸入位元組*串流*並將它們儲存在*緩衝區*. 與相關聯的檔案指標*資料流*（如果有的話） 會增加實際讀取的位元組數目。 如果指定的資料流以開啟[文字模式](../../c-runtime-library/text-and-binary-mode-file-i-o.md)，Windows 樣式的換行符號會轉換成 Unix 樣式的換行符號。 也就是歸位字元復位換行 (CRLF) 組是由單一換行字元 (LF) 字元所取代。 這種取代不會影響檔案指標或傳回值。 發生錯誤時，無法確定檔案指標位置。 無法判斷部分讀取項目的值。

使用文字模式資料流，如果要求的資料量時 (亦即*大小* \* *計數*) 大於或等於內部**檔案** \*緩衝區大小 (根據預設，這是 4096 個位元組，使用可設定[setvbuf](../../c-runtime-library/reference/setvbuf.md))、 資料流資料會直接複製到使用者所提供的緩衝區和新行字元的轉換已完成該緩衝區。 因為已轉換的資料可能會短於資料流資料複製到緩衝區，也就是過去的資料*緩衝區*\[*return_value* \* *大小*] (何處*return_value*傳回的值從**fread**) 可能包含未轉換的資料，從檔案。 基於這個理由，我們建議您以 null 結束的字元資料，在*緩衝區*\[*return_value* \* *大小*] 如果緩衝區的目的是若要做為 C 樣式字串。 請參閱[fopen](fopen-wfopen.md)如需詳細資訊，在文字模式和二進位模式的效果。

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
[文字和二進位檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
[fopen](fopen-wfopen.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
