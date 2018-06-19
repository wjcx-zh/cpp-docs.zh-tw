---
title: setbuf | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- setbuf
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
- setbuf
dev_langs:
- C++
helpviewer_keywords:
- setbuf function
- stream buffering
ms.assetid: 13beda22-7b56-455d-8a6c-f2eb636885b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f8592e8008fa78402ced307b60188ea8610960a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407310"
---
# <a name="setbuf"></a>setbuf

控制資料流緩衝處理。 已取代此函式；請改用 [setvbuf](setvbuf.md)。

## <a name="syntax"></a>語法

```C
void setbuf(
   FILE *stream,
   char *buffer
);
```

### <a name="parameters"></a>參數

*資料流*指標**檔案**結構。

*緩衝區*使用者配置的緩衝區。

## <a name="remarks"></a>備註

**Setbuf**函式控制項緩衝*資料流*。 *資料流*引數必須參考尚未讀取或寫入的開啟檔案。 如果*緩衝區*引數是**NULL**，是未緩衝的資料流。 如果沒有，緩衝區必須指向字元陣列的長度**BUFSIZ**，其中**BUFSIZ** STDIO 中定義為緩衝區大小。H. 使用者指定的緩衝區 (而非指定資料流的預設系統配置緩衝區) 用於 I/O 緩衝處理。 **Stderr**資料流是根據預設，未經過緩衝處理，但是您可以使用**setbuf**指派緩衝區**stderr**。

**setbuf**已被取代[setvbuf](setvbuf.md)，這是慣用的常式，以新的程式碼。 **setbuf**保留與現有的程式碼的相容性。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**setbuf**|\<stdio.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_setbuf.c
// compile with: /W3
// This program first opens files named DATA1 and
// DATA2. Then it uses setbuf to give DATA1 a user-assigned
// buffer and to change DATA2 so that it has no buffer.

#include <stdio.h>

int main( void )
{
   char buf[BUFSIZ];
   FILE *stream1, *stream2;

   fopen_s( &stream1, "data1", "a" );
   fopen_s( &stream2, "data2", "w" );

   if( (stream1 != NULL) && (stream2 != NULL) )
   {
      // "stream1" uses user-assigned buffer:
      setbuf( stream1, buf ); // C4996
      // Note: setbuf is deprecated; consider using setvbuf instead
      printf( "stream1 set to user-defined buffer at: %Fp\n", buf );

      // "stream2" is unbuffered
      setbuf( stream2, NULL ); // C4996
      printf( "stream2 buffering disabled\n" );
      _fcloseall();
   }
}
```

```Output
stream1 set to user-defined buffer at: 0012FCDC
stream2 buffering disabled
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[setvbuf](setvbuf.md)<br/>
