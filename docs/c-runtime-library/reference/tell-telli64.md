---
title: _tell、_telli64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _telli64
- _tell
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
- tell
- telli64
- _telli64
- _tell
dev_langs:
- C++
helpviewer_keywords:
- tell function
- file pointers [C++], getting
- _tell function
- file pointers [C++]
- telli64 function
- _telli64 function
ms.assetid: 1500e8f9-8fec-4253-9eec-ec66125dfc9b
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 85586a4c0c3a1a035dc4ccb1d36b2fed415220cd
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="tell-telli64"></a>_tell、_telli64

取得檔案指標的位置。

## <a name="syntax"></a>語法

```C
long _tell(
   int handle
);
__int64 _telli64(
   int handle
);
```

### <a name="parameters"></a>參數

*控制代碼*<br/>
參考已開啟檔案的檔案描述項。

## <a name="return-value"></a>傳回值

檔案指標的目前位置。 在無法搜尋的裝置上，傳回的值為未定義。

傳回-1l; 此時的值會指出錯誤。 如果*處理*是無效的檔案描述項無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會將**errno**至**EBADF**並傳回-1l; 此時。

如需這個及其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。

## <a name="remarks"></a>備註

**_Tell**函式取得目前位置的檔案指標 （如果有的話） 相關聯*處理*引數。 位置是以從檔案開頭的位元組數目來表示。 如 **_telli64**函式，這個值會表示為 64 位元整數。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_tell**， **_telli64**|\<io.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_tell.c
// This program uses _tell to tell the
// file pointer position after a file read.
//

#include <io.h>
#include <stdio.h>
#include <fcntl.h>
#include <share.h>
#include <string.h>

int main( void )
{
   int  fh;
   char buffer[500];

   if ( _sopen_s( &fh, "crt_tell.txt", _O_RDONLY, _SH_DENYNO, 0) )
   {
      char buff[50];
      _strerror_s( buff, sizeof(buff), NULL );
      printf( buff );
      exit( -1 );
   }

   if( _read( fh, buffer, 500 ) > 0 )
      printf( "Current file position is: %d\n", _tell( fh ) );
   _close( fh );
}
```

### <a name="input-crttelltxt"></a>輸入︰crt_tell.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>輸出

```Output
Current file position is: 20
```

## <a name="see-also"></a>另請參閱

[低層級 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[ftell、_ftelli64](ftell-ftelli64.md)<br/>
[_lseek、_lseeki64](lseek-lseeki64.md)<br/>
