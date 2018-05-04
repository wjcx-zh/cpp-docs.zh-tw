---
title: perror、_wperror | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wperror
- perror
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wperror
- _tperror
- perror
dev_langs:
- C++
helpviewer_keywords:
- _tperror function
- tperror function
- wperror function
- error messages, printing
- printing error messages
- _wperror function
- perror function
ms.assetid: 34fce792-16fd-4673-9849-cd88b54b6cd5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 455bf63cdac425217c40068853b302edefb94f16
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="perror-wperror"></a>perror、_wperror

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

*訊息*列印的字串訊息。

## <a name="remarks"></a>備註

**Perror**函式會列印錯誤訊息至**stderr**。 **_wperror**是寬字元版本的 **_perror**;*訊息*引數 **_wperror**是寬字元字串。 **_wperror**和 **_perror**除此之外的行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tperror**|**perror**|**perror**|**_wperror**|

*訊息*會列印第一次後, 接冒號，然後是系統錯誤訊息，取得產生錯誤，最後一次程式庫呼叫，最後由新行字元。 如果*訊息*為 null 指標或 null 字串的指標**perror**會列印只有系統錯誤訊息。

錯誤號碼會儲存在變數 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 中 (定義於 ERRNO.H 中)。 系統錯誤訊息是透過變數 [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 來存取，這是依錯誤號碼排序的訊息陣列。 **perror**適當的錯誤訊息使用列印**errno**為的索引值 **_sys_errlist**。 變數的值[_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)定義中的項目數目上限為 **_sys_errlist**陣列。

針對精確的結果，呼叫**perror**之後立即在程式庫常式傳回錯誤。 否則，後續呼叫可能會覆寫**errno**值。

在 Windows 作業系統，有些**errno** ERRNO 中列出的值。H 是未使用。 這些值會保留供 UNIX 作業系統使用。 請參閱[_doserrno，errno，_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)如的清單**errno** Windows 作業系統所使用的值。 **perror**列印任何空字串**errno**值不是由這些平台。

## <a name="requirements"></a>需求

|常式|必要的標頭|
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
