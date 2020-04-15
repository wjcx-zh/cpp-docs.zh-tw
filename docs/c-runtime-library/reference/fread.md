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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 26ffd56072f1a5fddc3131a42cd47c145e437b60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346057"
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

*大小*<br/>
項目大小 (位元組)。

*count*<br/>
要讀取項目的最大數量。

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

**fread**傳回實際讀取的完整項目,如果發生錯誤或在達到*計數*之前遇到檔案結尾,則可能小於*計數*。 使用**feof**或**ferror**函數來區分讀取錯誤和檔案結尾條件。 如果*大小*或*計數*為 0,**則 fread**返回 0,緩衝區內容保持不變。 如果*流*或*緩衝區*是空指標,**則 fread**將調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,此函數將**errno**設置到**EINVAL**並返回0。

有關這些錯誤代碼的詳細資訊[\_,請參閱劑\_量\_諾 、errno、sys\_errlist 和 sys\_nerr。](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>備註

**fread**函數最多讀取*以從輸入流中計數**大小**stream*位元組項, 並將其存儲在*緩衝區*中。 與*流*關聯的檔指標(如果有)由實際讀取的位元組數增加。 如果在[文字模式下](../../c-runtime-library/text-and-binary-mode-file-i-o.md)打開給定的流,Windows 樣式的換行將轉換為 Unix 樣式的換行。 也就是說,滑車回饋送 (CRLF) 對由單行饋送 (LF) 字元替換。 這種取代不會影響檔案指標或傳回值。 發生錯誤時，無法確定檔案指標位置。 無法判斷部分讀取項目的值。

在文字模式流上使用時,如果請求的數據量(即*大小*\**計數*)大於或等於內部**FILE**\*緩衝區大小(預設情況下為 4096 位元組,使用[setvbuf](../../c-runtime-library/reference/setvbuf.md)可配置),則流數據將直接複製到使用者提供的緩衝區中,並在該緩衝區中完成換行。 由於轉換後的數據可能比複製到緩衝區中的流數據短,因此超過*緩衝區*\[*的數據return_value*\**大小** (其中*return_value*是從**sread**返回值)可能包含檔中未轉換的數據。 因此,如果緩衝區的意圖用作 C 樣式字串,我們建議您在*緩衝區*\[*return_value*\**大小*下終止字元數據。 有關文本模式和二進位模式效果的詳細資訊,請參閱[fopen。](fopen-wfopen.md)

此函式會鎖定其他執行緒。 如果需要非鎖定版本,請使用 **_fread_nolock**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

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
[文字與二進位檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
[fopen](fopen-wfopen.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
