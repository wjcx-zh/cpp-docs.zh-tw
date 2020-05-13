---
title: fread
ms.date: 4/2/2020
api_name:
- fread
- _o_fread
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fread
helpviewer_keywords:
- reading data [C++], from input streams
- fread function
- data [C++], reading from input stream
- streams [C++], reading data from
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
ms.openlocfilehash: ec5af25070e253f6c04d1aab13404306251ed716
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912703"
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

*緩衝區*<br/>
資料的儲存位置。

*size*<br/>
項目大小 (位元組)。

*計數*<br/>
要讀取項目的最大數量。

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

**fread**會傳回實際讀取的完整專案數，如果發生錯誤，或在到達*計數*之前遇到檔案結尾，則可能少於*計數*。 使用**feof**或**ferror**函式來區別讀取錯誤與檔案結尾條件。 如果*size*或*count*為0，則**fread**會傳回0，而緩衝區內容則不會變更。 如果*stream*或*buffer*是 null 指標， **fread**會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會將**errno**設定為**EINVAL** ，並傳回0。

如需這些錯誤碼的詳細資訊，請參閱[ \_doserrno、errno、 \_sys\_errlist 和\_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。

## <a name="remarks"></a>備註

**Fread**函式會從輸入*資料流程*讀取*大小**為位元組的專案，* 並將它們儲存在*buffer*中。 與*資料流程*相關聯的檔案指標（如果有的話）會隨著實際讀取的位元組數而增加。 如果在[文字模式](../../c-runtime-library/text-and-binary-mode-file-i-o.md)中開啟給定的資料流程，Windows 樣式的分行符號會轉換成 Unix 樣式的分行符號。 也就是，換行字元換行（CRLF）會由單行換行字元（LF）取代。 這種取代不會影響檔案指標或傳回值。 發生錯誤時，無法確定檔案指標位置。 無法判斷部分讀取項目的值。

在文字模式串流上使用時，如果所要求的資料量（也就是，*大小* \* *計數*）大於或**等於內部檔案** \*緩衝區大小（根據預設，這是4096個位元組，可使用[setvbuf](../../c-runtime-library/reference/setvbuf.md)來設定），資料流程資料會直接複製到使用者提供的緩衝區，而在該緩衝區中進行的新行轉換。 因為轉換的資料可能會比複製到緩衝區的資料流程資料短，所以資料過去的*緩衝區*\[*return_value* \* *大小*] （其中*return_value*是**fread**的傳回值）可能包含檔案中未轉換的資料。 基於這個理由，如果緩衝區的目的是做為 C 樣式字串，建議您在*buffer*\[*return_value* \* *size*] 以 null 終止字元資料。 如需文字模式和二進位模式效果的詳細資訊，請參閱[fopen](fopen-wfopen.md) 。

此函式會鎖定其他執行緒。 如果您需要非鎖定版本，請使用 **_fread_nolock**。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**fread**|\<stdio.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
[文字和二進位檔案 i/o](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
[fopen](fopen-wfopen.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
