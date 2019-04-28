---
title: fgetpos
ms.date: 11/04/2016
apiname:
- fgetpos
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
- fgetpos
helpviewer_keywords:
- fgetpos function
- streams, file position indicator
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
ms.openlocfilehash: e213c9830ffe6edf04b12a80828f14cc48f77524
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333926"
---
# <a name="fgetpos"></a>fgetpos

取得資料流的檔案位置指標。

## <a name="syntax"></a>語法

```C
int fgetpos(
   FILE *stream,
   fpos_t *pos
);
```

### <a name="parameters"></a>參數

*stream*<br/>
目標資料流。

*pos*<br/>
位置指標儲存區。

## <a name="return-value"></a>傳回值

如果成功， **fgetpos**會傳回 0。 在失敗時，它會傳回非零值，並設定**errno**的下列其中一個資訊清單常數 （定義於 STDIO。H):**EBADF**，這表示指定的資料流不是有效的檔案指標或無法存取，或**EINVAL**，這表示*串流*值或值*pos*是無效的例如，如果不是 null 指標。 如果*資料流*或是*pos*會**NULL**指標，函式會叫用無效參數處理常式，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>備註

**Fgetpos**函式會取得目前的值*串流*引數的檔案位置指標和它的物件中所指向的存放區*pos*。**Fsetpos**函式稍後可以使用資訊儲存在*pos*重設*串流*次其位置的引數的指標**fgetpos**呼叫。 *Pos*值會以內部格式儲存，並僅適用於**fgetpos**並**fsetpos**。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**fgetpos**|\<stdio.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_fgetpos.c
// This program uses fgetpos and fsetpos to
// return to a location in a file.

#include <stdio.h>

int main( void )
{
   FILE   *stream;
   fpos_t pos;
   char   buffer[20];

   if( fopen_s( &stream, "crt_fgetpos.txt", "rb" ) ) {
      perror( "Trouble opening file" );
      return -1;
   }

   // Read some data and then save the position.
   fread( buffer, sizeof( char ), 8, stream );
   if( fgetpos( stream, &pos ) != 0 ) {
      perror( "fgetpos error" );
      return -1;
   }

   fread( buffer, sizeof( char ), 13, stream );
   printf( "after fgetpos: %.13s\n", buffer );

   // Restore to old position and read data
   if( fsetpos( stream, &pos ) != 0 ) {
      perror( "fsetpos error" );
      return -1;
   }

   fread( buffer, sizeof( char ), 13, stream );
   printf( "after fsetpos: %.13s\n", buffer );
   fclose( stream );
}
```

## <a name="input-crtfgetpostxt"></a>輸入：crt_fgetpos.txt

```Input
fgetpos gets a stream's file-position indicator.
```

### <a name="output-crtfgetpostxt"></a>輸出 crt_fgetpos.txt

```Output
after fgetpos: gets a stream
after fsetpos: gets a stream
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fsetpos](fsetpos.md)<br/>
