---
title: _futime、_futime32、_futime64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _futime64
- _futime32
- _futime
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- futime
- _futime
- futime64
- _futime64
dev_langs:
- C++
helpviewer_keywords:
- _futime function
- futime32 function
- futime64 function
- file modification time [C++]
- _futime64 function
- futime function
- _futime32 function
ms.assetid: b942ce8f-5cc7-4fa8-ab47-de5965eded53
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cdd7b68ac9e3bf55f64b9a68f7b8075eab640faa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056816"
---
# <a name="futime-futime32-futime64"></a>_futime、_futime32、_futime64

設定已開啟之檔案的修改時間。

## <a name="syntax"></a>語法

```C
int _futime(
   int fd,
   struct _utimbuf *filetime
);
int _futime32(
   int fd,
   struct __utimbuf32 *filetime
);
int _futime64(
   int fd,
   struct __utimbuf64 *filetime
);
```

### <a name="parameters"></a>參數

*fd*<br/>
已開啟之檔案的檔案描述元。

*filetime*<br/>
包含新修改日期之結構的指標。

## <a name="return-value"></a>傳回值

如果成功，則傳回 0。 發生錯誤時，會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函數會傳回-1 及**errno**設為**EBADF**，表示檔案描述項無效，或**EINVAL**，表示無效參數。

## <a name="remarks"></a>備註

**_Futime**常式相關聯的開啟檔案上設定的修改日期和存取時間*fd*。 **_futime**等同於[_utime](utime-utime32-utime64-wutime-wutime32-wutime64.md)，不同之處在於其引數是開啟的檔案，檔案描述元，而不是檔案或檔案的路徑名稱。 **_Utimbuf**結構包含新修改日期和存取時間的欄位。 這兩個欄位必須包含有效的值。 **_utimbuf32**並 **_utimbuf64**等於 **_utimbuf**分別使用 32 位元和 64 位元時間類型，除非。 **_futime**並 **_utimbuf**使用 64 位元時間類型與 **_futime**完全相同的行為 **_futime64**。 如果您需要強制進行舊行為，定義 **_USE_32BIT_TIME_T**。 如此一來，這會導致 **_futime**相同的行為 **_futime32** ，並造成 **_utimbuf**結構使用 32 位元時間類型，使其相當於 **__utimbuf32**。

**_futime64**，它會使用 **__utimbuf64**結構，可以讀取和修改檔案日期至 23:59:59，3000 年 12 月 31 日 UTC; 而呼叫 **_futime32**如果檔案的日期會失敗晚於 23:59:59 2038 年 1 月 18 日 UTC。 1970 年 1 月 1 日午夜是這些函式的日期範圍下限。

## <a name="requirements"></a>需求

|功能|必要的標頭|選擇性標頭|
|--------------|---------------------|---------------------|
|**_futime**|\<sys/utime.h>|\<errno.h>|
|**_futime32**|\<sys/utime.h>|\<errno.h>|
|**_futime64**|\<sys/utime.h>|\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_futime.c
// This program uses _futime to set the
// file-modification time to the current time.

#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <io.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <sys/utime.h>
#include <share.h>

int main( void )
{
   int hFile;

   // Show file time before and after.
   system( "dir crt_futime.c_input" );

   _sopen_s( &hFile, "crt_futime.c_input", _O_RDWR, _SH_DENYNO, 0 );

   if( _futime( hFile, NULL ) == -1 )
      perror( "_futime failed\n" );
   else
      printf( "File time modified\n" );

   _close (hFile);

   system( "dir crt_futime.c_input" );
}
```

### <a name="input-crtfutimecinput"></a>輸入︰crt_futime.c_input

```Input
Arbitrary file contents.
```

### <a name="sample-output"></a>範例輸出

```Output
Volume in drive Z has no label.
Volume Serial Number is 5C68-57C1

Directory of Z:\crt

03/25/2004  10:40 AM                24 crt_futime.c_input
               1 File(s)             24 bytes
               0 Dir(s)  24,268,476,416 bytes free
Volume in drive Z has no label.
Volume Serial Number is 5C68-57C1

Directory of Z:\crt

03/25/2004  10:41 AM                24 crt_futime.c_input
               1 File(s)             24 bytes
               0 Dir(s)  24,268,476,416 bytes free
File time modified
```

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
