---
title: setvbuf
ms.date: 4/2/2020
api_name:
- setvbuf
- _o_setvbuf
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
- setvbuf
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
ms.openlocfilehash: 203265a8dd85854bcedd737359b856fdc4cce04d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316256"
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

*緩衝區*<br/>
使用者配置的緩衝區。

*模式*<br/>
緩衝處理的模式。

*大小*<br/>
緩衝區大小 (以位元組為單位)。 允許範圍:2 個<=*大小*<= INT_MAX (2147483647)。 在內部,為*大小*提供的值向下舍入到最接近的倍數 2。

## <a name="return-value"></a>傳回值

若成功，即傳回 0。

如果*串*流為**NULL**,或者*模式*或*大小*不在有效的更改範圍內,則呼叫無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會傳回 -1，並將 **errno** 設為 **EINVAL**。

如需這些錯誤碼和其他錯誤碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**setvbuf**函數允許程式控制*串流的*緩衝和緩衝區大小。 *流*必須引用自打開以來未經過 I/O 操作的打開檔。 *緩衝區*指向的陣列用作緩衝區,除非它是**NULL,** 在這種情況下**setvbuf**使用\*長度*大小*/2 2 位元組的自動分配的緩衝區。

模式必須 **_IOFBF、_IOLBF****_IOLBF**或 **_IONBF**。 如果*模式***為_IOFBF**或 **_IOLBF**,則*大小*用作緩衝區的大小。 如果 *_IONBF模式***,則**流將取消緩衝,並忽略*大小*和*緩衝區*。 *模式*及其含義的值包括:

|*模式*值|意義|
|-|-|
| **_IOFBF** | 完全緩衝;也就是說,*緩衝區*用作緩衝區,*大小*用作緩衝區的大小。 如果*緩衝區*為**NULL,** 則使用自動分配的緩衝區*大小*位元組長。 |
| **_IOLBF** | 對於某些系統，這提供行緩衝處理。 但是,對於 Win32,該行為與 **_IOFBF** - 完全緩衝相同。 |
| **_IONBF** | 無論緩衝區或*大小*如何,都不使用*緩衝區*。 |

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
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
