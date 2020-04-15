---
title: _futime、_futime32、_futime64
ms.date: 4/2/2020
api_name:
- _futime64
- _futime32
- _futime
- _o__futime32
- _o__futime64
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- futime
- _futime
- futime64
- _futime64
helpviewer_keywords:
- _futime function
- futime32 function
- futime64 function
- file modification time [C++]
- _futime64 function
- futime function
- _futime32 function
ms.assetid: b942ce8f-5cc7-4fa8-ab47-de5965eded53
ms.openlocfilehash: 1f60bb3b366c48e3d53368f81ebc2528694794f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345496"
---
# <a name="_futime-_futime32-_futime64"></a>_futime、_futime32、_futime64

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

*Fd*<br/>
已開啟之檔案的檔案描述元。

*檔案時間*<br/>
包含新修改日期之結構的指標。

## <a name="return-value"></a>傳回值

如果成功，則傳回 0。 發生錯誤時，會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則函數返回 **-1,errno**設置為**EBADF,** 指示無效的檔描述符或**EINVAL**,指示無效參數。

## <a name="remarks"></a>備註

**_futime**例程設定與*fd*關聯的打開檔中的修改日期和訪問時間。 **_futime**與[_utime](utime-utime32-utime64-wutime-wutime32-wutime64.md)相同,只不過其參數是打開檔的檔案描述符,而不是檔的名稱或檔的路徑。 **_utimbuf**結構包含新修改日期和訪問時間的欄位。 這兩個欄位必須包含有效的值。 **_utimbuf32**和 **_utimbuf64**與 **_utimbuf**相同,但分別使用 32 位元和 64 位元時間類型。 **_futime**和 **_utimbuf**使用 64 位元時間類型 **,_futime**的行為與 **_futime64**相同。 如果需要強制舊行為,請定義 **_USE_32BIT_TIME_T**。 這樣做會導致 **_futime**行為與 **_futime32**相同,並導致 **_utimbuf**結構使用 32 位元時間類型,使其等效於 **__utimbuf32**。

**_futime64**()使用 **__utimbuf64**結構,可以在 UTC 12 月 31 日 23:59:59 讀取和修改檔日期;如果檔上的日期晚於 2038 年 1 月 18 日 23:59:59,UTC,則對 **_futime32**的調用將失敗。 1970 年 1 月 1 日午夜是這些函式的日期範圍下限。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|選擇性標頭|
|--------------|---------------------|---------------------|
|**_futime**|\<sys/utime.h>|\<errno.h>|
|**_futime32**|\<sys/utime.h>|\<errno.h>|
|**_futime64**|\<sys/utime.h>|\<errno.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

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

### <a name="input-crt_futimec_input"></a>輸入︰crt_futime.c_input

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
