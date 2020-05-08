---
title: ftell、_ftelli64
ms.date: 4/2/2020
api_name:
- _ftelli64
- ftell
- _o__ftelli64
- _o_ftell
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
- _ftelli64
- ftell
helpviewer_keywords:
- ftell function
- ftelli64 function
- _ftelli64 function
- file pointers [C++], getting current position
- file pointers [C++]
ms.assetid: 40149cd8-65f2-42ff-b70c-68e3e918cdd7
ms.openlocfilehash: 273ad4990f78355029770e19e7cdcf36d7ba39bf
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910069"
---
# <a name="ftell-_ftelli64"></a>ftell、_ftelli64

取得檔案指標的目前位置。

## <a name="syntax"></a>語法

```C
long ftell(
   FILE *stream
);
__int64 _ftelli64(
   FILE *stream
);
```

### <a name="parameters"></a>參數

*資料流*<br/>
目標**檔案**結構。

## <a name="return-value"></a>傳回值

**ftell**和 **_ftelli64**會傳回目前的檔案位置。 **Ftell**和 **_ftelli64**所傳回的值可能不會反映在文字模式中開啟之資料流程的實體位元組位移，因為文字模式會導致換行字元的翻譯。 使用**ftell**搭配[fseek](fseek-fseeki64.md)或 **_ftelli64**搭配[_fseeki64](fseek-fseeki64.md) ，以正確地返回檔案位置。 發生錯誤時， **ftell**和 **_ftelli64**會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回-1L，並將**errno**設定為 errno 中定義的兩個常數之一。H. **EBADF**常數表示*資料流程*引數不是有效的檔案指標值，或未參考開啟的檔案。 **EINVAL**表示傳遞給函數的*資料流程*引數無效。 在無法搜尋的裝置上（例如終端機和印表機），或當*stream*未參考到開啟的檔案時，傳回值為未定義。

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱[_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。

## <a name="remarks"></a>備註

**Ftell**和 **_ftelli64**函式會抓取與*資料流程*相關聯的檔案指標（如果有的話）的目前位置。 位置以相對於資料流開頭的位移表示。

請注意，檔案因為附加資料而開啟時，目前的檔案位置取決於最後一個 I/O 作業，而不是下一次寫入的位置。 例如，如果開啟檔案以供附加，而最後一個作業為讀取，該檔案的位置是下一個讀取作業會開始的位置，而不是下一次寫入的開始位置。 （開啟檔案以供附加時，會先將檔案位置移至檔案結尾，再進行任何寫入作業）。如果開啟要附加的檔案上尚未發生任何 i/o 作業，檔案位置就是檔案的開頭。

在文字模式中，Ctrl+Z 會在輸入時被解譯成檔案結尾字元。 在為了讀取/寫入而開啟的檔案中， **fopen**和所有相關的常式會檢查檔案結尾是否有 CTRL + Z，並盡可能加以移除。 這是因為使用**ftell**和[fseek](fseek-fseeki64.md)或 **_ftelli64**和[_fseeki64](fseek-fseeki64.md)的組合，在以 CTRL + Z 結束的檔案內移動可能會造成**ftell**或 **_ftelli64**的行為不正確，接近檔案結尾。

此函式執行期間會鎖定呼叫執行緒，因此為安全執行緒。 如需非鎖定版本，請參閱 **_ftell_nolock**。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|選擇性標頭|
|--------------|---------------------|----------------------|
|**ftell**|\<stdio.h>|\<errno.h>|
|**_ftelli64**|\<stdio.h>|\<errno.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_ftell.c
// This program opens a file named CRT_FTELL.C
// for reading and tries to read 100 characters. It
// then uses ftell to determine the position of the
// file pointer and displays this position.

#include <stdio.h>

FILE *stream;

int main( void )
{
   long position;
   char list[100];
   if( fopen_s( &stream, "crt_ftell.c", "rb" ) == 0 )
   {
      // Move the pointer by reading data:
      fread( list, sizeof( char ), 100, stream );
      // Get position after read:
      position = ftell( stream );
      printf( "Position after trying to read 100 bytes: %ld\n",
              position );
      fclose( stream );
   }
}
```

```Output
Position after trying to read 100 bytes: 100
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[fgetpos](fgetpos.md)<br/>
[fseek、_fseeki64](fseek-fseeki64.md)<br/>
[_lseek、_lseeki64](lseek-lseeki64.md)<br/>
