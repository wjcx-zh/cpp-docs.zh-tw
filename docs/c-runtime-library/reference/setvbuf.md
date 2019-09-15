---
title: setvbuf
ms.date: 11/04/2016
api_name:
- setvbuf
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
ms.openlocfilehash: 38b6474f550107a8edd941c7112ba98891ab3c12
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948187"
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

*stream*<br/>
**FILE** 結構的指標。

*buffer*<br/>
使用者配置的緩衝區。

*mode*<br/>
緩衝處理的模式。

*size*<br/>
緩衝區大小 (以位元組為單位)。 允許的範圍：2 < =*大小*< = INT_MAX （2147483647）。 就內部而言，針對*size*提供的值會四捨五入到最接近的倍數（共2個）。

## <a name="return-value"></a>傳回值

如果成功，會傳回 0。

如果*stream*為**Null**，或如果*模式*或*大小*不在有效的變更中，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會傳回 -1，並將 **errno** 設為 **EINVAL**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Setvbuf**函數可讓程式同時控制*資料流程*的緩衝和緩衝區大小。 *資料流程*必須參考開啟的檔案，而該檔案尚未在 i/o 作業開啟後進行。 *Buffer*所指向的陣列會當做緩衝區使用，除非它是**Null**，在此情況下， **setvbuf**會使用長度*大小*/2 \* 2 位元組的自動設定緩衝區。

此模式必須是 **_IOFBF**、 **_IOLBF**或 **_IONBF**。 如果*mode*為 **_IOFBF**或 **_IOLBF**，則*size*會當做緩衝區的大小使用。 如果*模式*為 **_IONBF**，則資料流程未緩衝，而且會忽略*大小*和*緩衝區*。 *Mode*的值和其意義如下：

|*模式*值|意義|
|-|-|
| **_IOFBF** | 完整緩衝;也就是說， *buffer*會當做緩衝區使用，而*大小*會當做緩衝區的大小使用。 如果*buffer*為**Null**，則會使用自動設定的緩衝區*大小*位元組長度。 |
| **_IOLBF** | 對於某些系統，這提供行緩衝處理。 不過，針對 Win32，行為與 **_IOFBF** -Full 緩衝相同。 |
| **_IONBF** | 無論*緩衝區*或*大小*為何，都不會使用任何緩衝區。 |

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
