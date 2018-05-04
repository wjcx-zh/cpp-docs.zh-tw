---
title: _setmode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _setmode
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
- _setmode
dev_langs:
- C++
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59aed27ec4803cd1709635da44ef37d748342e29
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="setmode"></a>_setmode

設定檔案轉譯模式。

## <a name="syntax"></a>語法

```C
int _setmode (
   int fd,
   int mode
);
```

### <a name="parameters"></a>參數

*fd*<br/>
檔案描述項。

*mode*<br/>
新的轉譯模式。

## <a name="return-value"></a>傳回值

若成功，會傳回之前的轉譯模式。

如果將無效參數傳遞至此函式，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若要繼續，此函數會傳回-1 和設定允許執行**errno**為**EBADF**，表示無效的檔案描述項，或**EINVAL**，表示無效*模式*引數。

如需有關這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Setmode**函式會將*模式*所提供檔案的轉譯模式*fd*。 傳遞 **_O_TEXT**為*模式*設定文字 （也就，已轉譯） 模式。 歸位字元傳回行摘要 (CR-LF) 組合會轉譯成單行換上輸入的字元。 換行字元會在輸出中轉譯為 CR-LF 組合。 傳遞 **_O_BINARY**設定二進位 （未轉譯） 模式，這些翻譯都會被隱藏。

您也可以傳遞 **_O_U16TEXT**， **_O_U8TEXT**，或 **_O_WTEXT**啟用 Unicode 模式，如本文稍後的第二個範例所示。 **_setmode**通常用來修改的預設轉譯模式**stdin**和**stdout**，但是您可以使用它的任何檔案上。 如果您套用 **_setmode**資料流的檔案描述項，呼叫 **_setmode**執行資料流上的任何輸入或輸出作業之前。

> [!CAUTION]
> 如果您資料寫入檔案資料流排清明確程式碼使用[fflush](fflush.md)使用之前 **_setmode**来變更的模式。 若您沒有清除代碼，可能會發生未預期的行為。 若您沒有將資料寫入資料流，則不用清除代碼。

## <a name="requirements"></a>需求

|常式|必要的標頭|選擇性標頭|
|-------------|---------------------|----------------------|
|**_setmode**|\<io.h>|\<fcntl.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_setmode.c
// This program uses _setmode to change
// stdin from text mode to binary mode.

#include <stdio.h>
#include <fcntl.h>
#include <io.h>

int main( void )
{
   int result;

   // Set "stdin" to have binary mode:
   result = _setmode( _fileno( stdin ), _O_BINARY );
   if( result == -1 )
      perror( "Cannot set mode" );
   else
      printf( "'stdin' successfully changed to binary mode\n" );
}
```

```Output
'stdin' successfully changed to binary mode
```

## <a name="example"></a>範例

```C
// crt_setmodeunicode.c
// This program uses _setmode to change
// stdout to Unicode. Cyrillic and Ideographic
// characters will appear on the console (if
// your console font supports those character sets).

#include <fcntl.h>
#include <io.h>
#include <stdio.h>

int main(void) {
    _setmode(_fileno(stdout), _O_U16TEXT);
    wprintf(L"\x043a\x043e\x0448\x043a\x0430 \x65e5\x672c\x56fd\n");
    return 0;
}
```

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_set_fmode](set-fmode.md)<br/>
