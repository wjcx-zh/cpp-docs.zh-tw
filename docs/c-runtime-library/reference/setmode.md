---
title: _setmode
ms.date: 11/04/2016
api_name:
- _setmode
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
- _setmode
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
ms.openlocfilehash: 7f14cc9451b93a9077916b8c650645990ba654a3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948583"
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

*fd*<br/>
檔案描述項。

*mode*<br/>
新的轉譯模式。

## <a name="return-value"></a>傳回值

若成功，會傳回之前的轉譯模式。

如果將無效參數傳遞至此函式，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會傳回-1，並將**errno**設定為**EBADF**（表示不正確檔案描述項）或**EINVAL**（表示不正確*模式*引數）。

如需有關這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Setmode**函數會將*fd*所提供之檔案的轉譯模式設定為*mode* 。 以*模式*傳遞 **_O_TEXT**會設定文字（也就是已轉譯）模式。 在輸入時，會將換行字元（CR-LF）組合轉譯成單一換行字元。 換行字元會在輸出中轉譯為 CR-LF 組合。 傳遞 **_O_BINARY**會設定二進位（未轉譯）模式，其中會抑制這些翻譯。

您也可以傳遞 **_O_U16TEXT**、 **_O_U8TEXT**或 **_O_WTEXT**來啟用 Unicode 模式，如本檔稍後的第二個範例所示。

> [!CAUTION]
> Unicode 模式適用于寬列印函式（例如） `wprintf`，不支援用於窄的列印功能。 在 Unicode 模式資料流程上使用窄的 print 函數會觸發判斷提示。

**_setmode**通常用來修改**stdin**和**stdout**的預設轉譯模式，但是您可以在任何檔案上使用它。 如果您將 **_setmode**套用至資料流程的檔案描述元，請在資料流程上執行任何輸入或輸出作業之前，先呼叫 **_setmode** 。

> [!CAUTION]
> 如果您將資料寫入檔案資料流程，請先使用[fflush](fflush.md)明確地清除程式碼，然後再使用 **_setmode**來變更模式。 若您沒有清除代碼，可能會發生未預期的行為。 若您沒有將資料寫入資料流，則不用清除代碼。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
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
