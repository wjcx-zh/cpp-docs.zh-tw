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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: bfe79610161a7f4032517d9f7eaa0de50be18e50
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345619"
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
目標**檔案結構**。

## <a name="return-value"></a>傳回值

**ftell**和 **_ftelli64**傳回目前的檔案位置。 **ftell**和 **_ftelli64**返回的值可能無法反映文本模式下打開的流的物理位元組偏移量,因為文本模式會導致回車換行轉換。 將**ftell**與[fseek](fseek-fseeki64.md)或 **_ftelli64**與[_fseeki64](fseek-fseeki64.md)正確返回到檔位置。 在錯誤時 **,ftell**和 **_ftelli64**呼叫無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,這些函數將返回 -1L 並將**errno**設置為在ERRNO中定義的兩個常量之一。H。 **EBADF**常量表示*流*參數不是有效的檔指標值,或者不引用打開的檔。 **EINVAL**表示無效*的流*參數已傳遞到函數。 在無法查找的設備(如終端和印表機)上,或者當*流*不引用打開的檔時,返回值未定義。

有關這些代碼和其他返回代碼的詳細資訊[,請參閱_doserrno、errno、_sys_errlist和_sys_nerr。](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>備註

**ftell**和 **_ftelli64**函數檢索與*流*關聯的檔指標(如果有)的當前位置。 位置以相對於資料流開頭的位移表示。

請注意，檔案因為附加資料而開啟時，目前的檔案位置取決於最後一個 I/O 作業，而不是下一次寫入的位置。 例如，如果開啟檔案以供附加，而最後一個作業為讀取，該檔案的位置是下一個讀取作業會開始的位置，而不是下一次寫入的開始位置。 (打開檔案進行追加時,檔位置將移動到檔末尾,然後再進行任何寫入操作。如果打開用於追加的檔尚未發生 I/O 操作,則檔位置是檔的開頭。

在文字模式中，Ctrl+Z 會在輸入時被解譯成檔案結尾字元。 在打開用於讀取/寫入的檔中 **,fopen**和所有相關例程檢查檔末尾的 CTRL_Z,並盡可能將其刪除。 這樣做是因為使用**ftell**和[fseek](fseek-fseeki64.md)或 **_ftelli64**和[_fseeki64](fseek-fseeki64.md)的組合,在以 CTRL_Z 結尾的檔內移動可能會導致**ftell**或 **_ftelli64**在檔末尾附近行為不當。

此函式執行期間會鎖定呼叫執行緒，因此為安全執行緒。 有關非鎖定版本,請參閱 **_ftell_nolock**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

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
