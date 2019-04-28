---
title: _getcwd、_wgetcwd
ms.date: 11/04/2016
apiname:
- _wgetcwd
- _getcwd
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getcwd
- wgetcwd
- _wgetcwd
- tgetcwd
- _tgetcwd
helpviewer_keywords:
- getcwd function
- working directory
- _wgetcwd function
- _getcwd function
- current working directory
- wgetcwd function
- directories [C++], current working
ms.assetid: 888dc8c6-5595-4071-be55-816b38e3e739
ms.openlocfilehash: 4c533f0e716cb9a13c152b9be3c46f60291118d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331788"
---
# <a name="getcwd-wgetcwd"></a>_getcwd、_wgetcwd

取得目前工作目錄。

## <a name="syntax"></a>語法

```C
char *_getcwd(
   char *buffer,
   int maxlen
);
wchar_t *_wgetcwd(
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>參數

*buffer*<br/>
路徑的儲存位置。

*maxlen*<br/>
路徑以字元為單位的最大長度： **char**如 **_getcwd**並**wchar_t**如 **_wgetcwd**。

## <a name="return-value"></a>傳回值

將指標傳回至*緩衝區*。 A **NULL**傳回值表示錯誤，並**errno**設為**ENOMEM**，表示記憶體不足，無法配置*maxlen*位元組 (當**NULL**引數指定為*緩衝區*)，或**ERANGE**，表示路徑長度超過*maxlen*字元。 如果*maxlen*小於或等於零，此函式會叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。

如需有關這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Getcwd**函式會取得預設磁碟機的目前工作目錄的完整路徑，並將其儲存在*緩衝區*。 整數引數*maxlen*指定路徑的最大長度。 如果路徑 （包括結束的 null 字元） 的長度超過，就會發生錯誤*maxlen*。 *緩衝區*引數可以是**NULL**; 緩衝區的大小至少*maxlen* （必要時才增加） 自動配置使用**malloc**來儲存路徑。 這個緩衝區稍後可以藉由呼叫釋放**免費**並將其傳遞 **_getcwd**傳回值 （已配置的緩衝區的指標）。

**_getcwd**傳回字串，表示目前的工作目錄的路徑。 如果目前的工作目錄是根目錄，字串結尾的反斜線 ( **\\** )。 如果目前的工作目錄是根目錄以外的目錄，字串會以目錄名稱結尾，而不是反斜線。

**_wgetcwd**是寬字元版本的 **_getcwd**;*緩衝區*引數和傳回值 **_wgetcwd**是寬字元字串。 **_wgetcwd**並 **_getcwd**行為相同。

當 **_DEBUG**並 **_CRTDBG_MAP_ALLOC**所定義，但呼叫 **_getcwd**和 **_wgetcwd**會取代藉由呼叫 **_getcwd_dbg**並 **_wgetcwd_dbg**以便進行偵錯記憶體配置。 如需詳細資訊，請參閱 [_getcwd_dbg、_wgetcwd_dbg](getcwd-dbg-wgetcwd-dbg.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd**|**_getcwd**|**_getcwd**|**_wgetcwd**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_getcwd**|\<direct.h>|
|**_wgetcwd**|\<direct.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_getcwd.c
// This program places the name of the current directory in the
// buffer array, then displays the name of the current directory
// on the screen. Passing NULL as the buffer forces getcwd to allocate
// memory for the path, which allows the code to support file paths
// longer than _MAX_PATH, which are supported by NTFS.

#include <direct.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char* buffer;

   // Get the current working directory:
   if( (buffer = _getcwd( NULL, 0 )) == NULL )
      perror( "_getcwd error" );
   else
   {
      printf( "%s \nLength: %d\n", buffer, strnlen(buffer) );
      free(buffer);
   }
}
```

```Output
C:\Code
```

## <a name="see-also"></a>另請參閱

[目錄控制](../../c-runtime-library/directory-control.md)<br/>
[_chdir、_wchdir](chdir-wchdir.md)<br/>
[_mkdir、_wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir、_wrmdir](rmdir-wrmdir.md)<br/>
