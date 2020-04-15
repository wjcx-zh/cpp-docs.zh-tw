---
title: _setmode
ms.date: 4/2/2020
api_name:
- _setmode
- _o__setmode
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
- _setmode
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
ms.openlocfilehash: 36d2130d4039f1f87f7f54fc26ad02cb8d519b4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353840"
---
# <a name="_setmode"></a>_setmode

設定檔案轉譯模式。

## <a name="syntax"></a>語法

```C
int _setmode (
   int fd,
   int mode
);
```

### <a name="parameters"></a>參數

*Fd*<br/>
檔案描述項。

*模式*<br/>
新的轉譯模式。

## <a name="return-value"></a>傳回值

若成功，會傳回之前的轉譯模式。

如果將無效參數傳遞至此函式，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,此函數將返回 -1 並將**errno**設置給**EBADF**,指示無效的檔描述符,或**EINVAL**,指示無效*的模式*參數。

如需這些傳回碼和其他傳回碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_setmode**函數集以*模式* *fd*給出的檔案的轉換模式。 傳遞 **_O_TEXT***模式*設定文字(即已翻譯)模式。 車廂返回線饋送 (CR-LF) 組合在輸入時轉換為單個換行字元。 換行字元會在輸出中轉譯為 CR-LF 組合。 傳遞 **_O_BINARY**設置二進位(未翻譯)模式,其中將抑制這些翻譯。

您還可以透過 **_O_U16TEXT、_O_U8TEXT****_O_U8TEXT**或 **_O_WTEXT**來啟用 Unicode 模式,本文件後面的第二個範例將展示。

> [!CAUTION]
> Unicode 模式適用於寬列印功能(例如),`wprintf`對於窄列印功能,不支援。 在 Unicode 模式流上使用窄列印函數會觸發斷言。

**_setmode**通常用於修改**stdin**和**stdout**的預設轉換模式,但您可以在任何檔上使用它。 如果將 **_setmode**應用於流的檔描述符,請**先調用_setmode,** 然後再對流執行任何輸入或輸出操作。

> [!CAUTION]
> 如果將資料寫入檔流,則在使用 **_setmode**更改模式之前,請使用[fflush](fflush.md)顯式刷新代碼。 若您沒有清除代碼，可能會發生未預期的行為。 若您沒有將資料寫入資料流，則不用清除代碼。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|----------------------|
|**_setmode**|\<io.h>|\<fcntl.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

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
