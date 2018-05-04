---
title: setvbuf | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- setvbuf
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
- setvbuf
dev_langs:
- C++
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c516932eb8d50fb8c9fdbe6f8c48a3f590b1ffb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="setvbuf"></a>setvbuf

控制資料流緩衝處理和緩衝區大小。

## <a name="syntax"></a>語法

```C
int setvbuf(
   FILE *stream,
   char *buffer,
   int mode,
   size_t size
);
```

### <a name="parameters"></a>參數

*資料流*<br/>
**FILE** 結構的指標。

*buffer*<br/>
使用者配置的緩衝區。

*mode*<br/>
緩衝處理的模式。

*size*<br/>
緩衝區大小 (以位元組為單位)。 允許範圍： 2 < =*大小*< = INT_MAX (2147483647)。 就內部而言，為提供的值*大小*無條件捨去到最接近 2 的倍數。

## <a name="return-value"></a>傳回值

如果成功，會傳回 0。

如果*資料流*是**NULL**，或如果*模式*或*大小*是不在有效的變更，無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，此函數會傳回-1 和設定允許執行**errno**至**EINVAL**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Setvbuf**函式可讓程式能夠控制這兩個緩衝和緩衝區大小*資料流*。 *資料流*必須參考自開啟後未經過 I/O 作業已開啟的檔案。 所指陣列*緩衝區*除非它是作為緩衝區， **NULL**的情況下**setvbuf**使用自動配置的緩衝區的長度*大小*/2 * 2 位元組。

模式必須是 **_IOFBF**， **_IOLBF**，或 **_IONBF**。 如果*模式*是 **_IOFBF**或 **_IOLBF**，然後*大小*做為緩衝區的大小。 如果*模式*是 **_IONBF**，資料流已緩衝和*大小*和*緩衝區*都會被忽略。 值*模式*和其意義：

|*模式*值|意義|
|-|-|
**_IOFBF**|完整的緩衝。也就是說，*緩衝區*做為緩衝區和*大小*做為緩衝區的大小。 如果*緩衝區*是**NULL**，自動配置的緩衝區*大小*使用的位元組長度。
**_IOLBF**|對於某些系統，這提供行緩衝處理。 不過，win32，行為是相同 **_IOFBF** -完整緩衝處理。
**_IONBF**|沒有緩衝區可使用，而不論*緩衝區*或*大小*。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**setvbuf**|\<stdio.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_setvbuf.c
// This program opens two streams: stream1
// and stream2. It then uses setvbuf to give stream1 a
// user-defined buffer of 1024 bytes and stream2 no buffer.
//

#include <stdio.h>

int main( void )
{
   char buf[1024];
   FILE *stream1, *stream2;

   if( fopen_s( &stream1, "data1", "a" ) == 0 &&
       fopen_s( &stream2, "data2", "w" ) == 0 )
   {
      if( setvbuf( stream1, buf, _IOFBF, sizeof( buf ) ) != 0 )
         printf( "Incorrect type or size of buffer for stream1\n" );
      else
         printf( "'stream1' now has a buffer of 1024 bytes\n" );
      if( setvbuf( stream2, NULL, _IONBF, 0 ) != 0 )
         printf( "Incorrect type or size of buffer for stream2\n" );
      else
         printf( "'stream2' now has no buffer\n" );
      _fcloseall();
   }
}
```

```Output
'stream1' now has a buffer of 1024 bytes
'stream2' now has no buffer
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[setbuf](setbuf.md)<br/>
