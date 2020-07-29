---
title: _getcwd、_wgetcwd
description: C 執行時間程式庫函數 _getcwd，_wgetcwd 取得目前的工作目錄。
ms.date: 4/2/2020
api_name:
- _wgetcwd
- _getcwd
- _o__getcwd
- _o__wgetcwd
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: b6fb32a593a969f93a934f251f38cd50960440b0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221883"
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

*緩衝區*\
路徑的儲存位置。

*maxlen*\
路徑的最大長度（以字元為單位）： **`char`** 適用于 **_getcwd** ，而 **`wchar_t`** 適用于 **_wgetcwd**。

## <a name="return-value"></a>傳回值

傳回*緩衝區*的指標。 **Null**傳回值表示錯誤，並將**Errno**設定為**ENOMEM**，表示記憶體不足，無法配置*maxlen*位元組（當**Null**引數指定為*buffer*時）或**ERANGE**，表示路徑長度超過*maxlen*個字元。 如果*maxlen*小於或等於零，則此函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。

如需這些傳回碼和其他傳回碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Getcwd**函式會取得預設磁片磁碟機之目前工作目錄的完整路徑，並將其儲存在*buffer*。 整數引數*maxlen*會指定路徑的最大長度。 如果路徑長度（包括終止的 null 字元）超過*maxlen*，就會發生錯誤。 *Buffer*引數可以是**Null**;至少具有*maxlen*大小的緩衝區（只在必要時才會使用**malloc**）來儲存路徑。 這個緩衝區稍後可以藉由呼叫**free**來釋放，並將 **_getcwd**傳回值（已配置緩衝區的指標）傳遞給它。

**_getcwd**會傳回代表目前工作目錄路徑的字串。 如果目前的工作目錄是根目錄，則字串的結尾會是反斜線（ `\` ）。 如果目前的工作目錄是根目錄以外的目錄，字串會以目錄名稱結尾，而不是反斜線。

**_wgetcwd**是寬字元版本的 **_getcwd**;**_wgetcwd**的*緩衝區*引數和傳回值是寬字元字串。 相反地， **_wgetcwd**和 **_getcwd**的行為相同。

定義 **_DEBUG**和 **_CRTDBG_MAP_ALLOC**時，對 **_getcwd**和 **_wgetcwd**的呼叫會被 **_getcwd_dbg**和 **_wgetcwd_dbg**的呼叫所取代，以允許進行記憶體配置的偵錯工具。 如需詳細資訊，請參閱 [_getcwd_dbg、_wgetcwd_dbg](getcwd-dbg-wgetcwd-dbg.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd**|**_getcwd**|**_getcwd**|**_wgetcwd**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_getcwd**|\<direct.h>|
|**_wgetcwd**|\<direct.h> 或 \<wchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_getcwd.c
// Compile with: cl /W4 crt_getcwd.c
// This program places the name of the current directory in the
// buffer array, then displays the name of the current directory
// on the screen. Passing NULL as the buffer forces getcwd to allocate
// memory for the path, which allows the code to support file paths
// longer than _MAX_PATH, which are supported by NTFS.

#include <direct.h> // _getcwd
#include <stdlib.h> // free, perror
#include <stdio.h>  // printf
#include <string.h> // strlen

int main( void )
{
   char* buffer;

   // Get the current working directory:
   if ( (buffer = _getcwd( NULL, 0 )) == NULL )
      perror( "_getcwd error" );
   else
   {
      printf( "%s \nLength: %zu\n", buffer, strlen(buffer) );
      free(buffer);
   }
}
```

```Output
C:\Code
```

## <a name="see-also"></a>另請參閱

[目錄控制](../../c-runtime-library/directory-control.md)\
[_chdir，_wchdir](chdir-wchdir.md)\
[_mkdir，_wmkdir](mkdir-wmkdir.md)\
[_rmdir、_wrmdir](rmdir-wrmdir.md)
