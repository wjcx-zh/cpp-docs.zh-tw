---
title: fgetpos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- fgetpos function
- streams, file position indicator
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b111a911083354c8d9478b2c914a0a5f7dfe7725
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397381"
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

*資料流*<br/>
目標資料流。

*pos*<br/>
位置指標儲存區。

## <a name="return-value"></a>傳回值

如果成功的話， **fgetpos**傳回 0。 如果失敗，它會傳回非零值，並設定**errno**的下列其中一個資訊清單常數 （定義於 STDIO。H): **EBADF**，這表示指定的資料流不是有效的檔案指標或無法存取，或**EINVAL**，這表示*資料流*值或值*pos*是無效的例如，如果不是 null 指標。 如果*資料流*或*pos*是**NULL**指標，函式會叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>備註

**Fgetpos**函式取得的目前值*資料流*引數的檔案位置指標，該物件中所指向的存放區*pos*。**Fsetpos**函式可以稍後使用資訊儲存在*pos*重設*資料流*時其位置引數的指標**fgetpos**呼叫。 *Pos*值會儲存在內部格式，並僅適用於**fgetpos**和**fsetpos**。

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
