---
title: _getcwd、_wgetcwd
ms.date: 11/04/2016
api_name:
- _wgetcwd
- _getcwd
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 78b02871aafca85db50df2eea74a2210c578c204
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955238"
---
# <a name="_getcwd-_wgetcwd"></a>_getcwd、_wgetcwd

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
路徑的最大長度（以字元為單位）： **char**代表 **_getcwd** ，而**wchar_t**代表 **_wgetcwd**。

## <a name="return-value"></a>傳回值

傳回*緩衝區*的指標。 **Null**傳回值表示錯誤，並將**Errno**設定為**ENOMEM**，表示記憶體不足，無法配置*maxlen*位元組（當**Null**引數指定為*buffer*時）或**ERANGE**，表示路徑長度超過*maxlen*個字元。 如果*maxlen*小於或等於零，則此函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。

如需有關這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Getcwd**函數會取得預設磁片磁碟機之目前工作目錄的完整路徑，並將其儲存在*buffer*。 整數引數*maxlen*會指定路徑的最大長度。 如果路徑長度（包括終止的 null 字元）超過*maxlen*，就會發生錯誤。 *Buffer*引數可以是**Null**;至少具有*maxlen*大小的緩衝區（只在必要時才會使用**malloc**）來儲存路徑。 這個緩衝區稍後可以藉由呼叫**free**來釋放，並將 **_getcwd**傳回值（已配置緩衝區的指標）傳遞給它。

**_getcwd**會傳回代表目前工作目錄路徑的字串。 如果目前的工作目錄是根目錄，則字串的結尾會是反斜線 **\\** （）。 如果目前的工作目錄是根目錄以外的目錄，字串會以目錄名稱結尾，而不是反斜線。

**_wgetcwd**是寬字元版本的 **_getcwd**; **_wgetcwd**的*buffer*引數和傳回值是寬字元字串。 相反地， **_wgetcwd**和 **_getcwd**的行為相同。

定義 **_debug**和 **_CRTDBG_MAP_ALLOC**時，對 **_getcwd**和 **_wgetcwd**的呼叫會被 **_getcwd_dbg**和 **_wgetcwd_dbg**的呼叫所取代，以允許進行記憶體配置的偵錯工具。 如需詳細資訊，請參閱 [_getcwd_dbg、_wgetcwd_dbg](getcwd-dbg-wgetcwd-dbg.md)。

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
