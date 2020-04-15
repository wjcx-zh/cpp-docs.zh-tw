---
title: _getcwd、_wgetcwd
description: C 運行時庫函數_getcwd,_wgetcwd獲取當前工作目錄。
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: bc19a416ebebeb901e8dbb435971e6d5f33e4067
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344438"
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

*馬克斯倫*\
以字元表示路徑的最大長度 **:_getcwd**的**字元****,_wgetcwd**的**wchar_t。**

## <a name="return-value"></a>傳回值

傳回於緩衝區的*指標*。 **NULL**傳回值指示錯誤 **,errno**設定為**ENOMEM,** 指示記憶體不足以分配*maxlen*位元組(當**NULL**參數作為*緩衝區*時)或**ERANGE,** 指示路徑長於*maxlen*字元。 如果*maxlen*小於或等於零,則此函數將調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。

如需這些傳回碼和其他傳回碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_getcwd**函數獲取預設驅動器當前工作目錄的完整路徑並將其存儲在*緩衝區*中。 整數參數*maxlen*指定路徑的最大長度。 如果路徑的長度(包括終止空字元)超過*maxlen,* 則會發生錯誤。 *緩衝區*參數可以是**NULL**;使用**malloc**自動分配至少大小*最大 len*的緩衝區(僅在必要時更多),以儲存路徑。 稍後可以通過調用**空閒**並傳遞 **_getcwd**返回值(指向已分配的緩衝區的指標)來釋放此緩衝區。

**_getcwd**返回表示當前工作目錄路徑的字串。 如果目前工作目錄是根目錄,則字串以反斜杠結束 。`\` 如果目前的工作目錄是根目錄以外的目錄，字串會以目錄名稱結尾，而不是反斜線。

**_wgetcwd**是 **_getcwd**的寬字元版本;*緩衝區*參數和 **_wgetcwd**的返回值是寬字元字串。 **_wgetcwd**和 **_getcwd**行為相同。

定義 **_DEBUG**和 **_CRTDBG_MAP_ALLOC**時,對 **_getcwd**和 **_wgetcwd**的調用將替換為對 **_getcwd_dbg**和 **_wgetcwd_dbg**的調用,以允許調試記憶體分配。 如需詳細資訊，請參閱 [_getcwd_dbg、_wgetcwd_dbg](getcwd-dbg-wgetcwd-dbg.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

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
[_wchdir,_chdir](chdir-wchdir.md)\
[_mkdir,_wmkdir](mkdir-wmkdir.md)\
[_rmdir、_wrmdir](rmdir-wrmdir.md)
