---
title: perror、_wperror
ms.date: 11/04/2016
api_name:
- _wperror
- perror
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wperror
- _tperror
- perror
helpviewer_keywords:
- _tperror function
- tperror function
- wperror function
- error messages, printing
- printing error messages
- _wperror function
- perror function
ms.assetid: 34fce792-16fd-4673-9849-cd88b54b6cd5
ms.openlocfilehash: 755b638f320fcc583faecfe6aa82269e4e1b3d8f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951026"
---
# <a name="perror-_wperror"></a>perror、_wperror

列印錯誤訊息。

## <a name="syntax"></a>語法

```C
void perror(
   const char *message
);
void _wperror(
   const wchar_t *message
);
```

### <a name="parameters"></a>參數

*message*<br/>
要列印的字串訊息。

## <a name="remarks"></a>備註

**Perror**函數會將錯誤訊息列印到**stderr**。 **_wperror**是寬字元版本的 **_perror**; **_wperror**的*訊息*引數是寬字元字串。 相反地， **_wperror**和 **_perror**的行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tperror**|**perror**|**perror**|**_wperror**|

*訊息*會先列印，後面接著冒號，然後是最後一次產生錯誤的程式庫呼叫的系統錯誤訊息，最後是分行符號。 如果*message*是 null 指標或 null 字串的指標， **perror**只會列印系統錯誤訊息。

錯誤號碼會儲存在變數 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 中 (定義於 ERRNO.H 中)。 系統錯誤訊息是透過變數 [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 來存取，這是依錯誤號碼排序的訊息陣列。 **perror**會使用**errno**值做為 **_sys_errlist**的索引，來列印適當的錯誤訊息。 變數[_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)的值定義為 **_sys_errlist**陣列中元素的最大數目。

如需精確的結果，請在程式庫常式傳回但發生錯誤時立即呼叫**perror** 。 否則，後續呼叫可能會覆寫**errno**值。

在 Windows 作業系統中，某些**errno**值列在 errno 中。H 未使用。 這些值會保留供 UNIX 作業系統使用。 如需 Windows 作業系統所使用之**errno**值的清單，請參閱[_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。 **perror**會針對這些平臺未使用的任何**errno**值，列印空字串。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**perror**|\<stdio.h> 或 \<stdlib.h>|
|**_wperror**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_perror.c
// compile with: /W3
/* This program attempts to open a file named
* NOSUCHF.ILE. Because this file probably doesn't exist,
* an error message is displayed. The same message is
* created using perror, strerror, and _strerror.
*/

#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <share.h>

int main( void )
{
   int  fh;

   if( _sopen_s( &fh, "NOSUCHF.ILE", _O_RDONLY, _SH_DENYNO, 0 ) != 0 )
   {
      /* Three ways to create error message: */
      perror( "perror says open failed" );
      printf( "strerror says open failed: %s\n",
         strerror( errno ) ); // C4996
      printf( _strerror( "_strerror says open failed" ) ); // C4996
      // Note: strerror and _strerror are deprecated; consider
      // using strerror_s and _strerror_s instead.
   }
   else
   {
      printf( "open succeeded on input file\n" );
      _close( fh );
   }
}
```

```Output
perror says open failed: No such file or directory
strerror says open failed: No such file or directory
_strerror says open failed: No such file or directory
```

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[strerror、_strerror、_wcserror、\__wcserror](strerror-strerror-wcserror-wcserror.md)<br/>
