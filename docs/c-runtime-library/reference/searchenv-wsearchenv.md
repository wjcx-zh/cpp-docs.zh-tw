---
title: _searchenv、_wsearchenv
ms.date: 11/04/2016
apiname:
- _searchenv
- _wsearchenv
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
apitype: DLLExport
f1_keywords:
- _wsearchenv
- _tsearchenv
- wsearchenv
- _searchenv
- searchenv
helpviewer_keywords:
- _wsearchenv function
- files [C++], finding
- _searchenv function
- tsearchenv function
- environment paths, searching for files
- _tsearchenv function
- wsearchenv function
- searchenv function
- environment paths
ms.assetid: 9c944a27-d326-409b-aee6-410e8762d9d3
ms.openlocfilehash: c1d2361fceec448c98fd9e5a368653aac38c83e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356767"
---
# <a name="searchenv-wsearchenv"></a>_searchenv、_wsearchenv

使用環境路徑來搜尋檔案。 這些函式已有更安全的版本可供使用，請參閱 [_searchenv_s、_wsearchenv_s](searchenv-s-wsearchenv-s.md)。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
void _searchenv(
   const char *filename,
   const char *varname,
   char *pathname
);
void _wsearchenv(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t *pathname
);
template <size_t size>
void _searchenv(
   const char *filename,
   const char *varname,
   char (&pathname)[size]
); // C++ only
template <size_t size>
void _wsearchenv(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t (&pathname)[size]
); // C++ only
```

### <a name="parameters"></a>參數

*filename*<br/>
要搜尋的檔案名稱。

*varname*<br/>
要搜尋的環境。

*pathname*<br/>
要儲存此完整路徑的緩衝區。

## <a name="remarks"></a>備註

**_Searchenv**例行搜尋指定的網域中的目標檔案。 *Varname*變數可以是任何環境或使用者定義變數 — 比方說，**路徑**， **LIB**，或**INCLUDE**— 指定目錄路徑的清單。 因為 **_searchenv**區分大小寫， *varname*應該符合環境變數的大小寫。

此常式會先搜尋目前工作目錄中的檔案。 如果找不到此檔案，便會在環境變數指定的目錄中尋找。 如果目標檔案已在其中一個這些目錄中，新建立的路徑會複製到*pathname*。 如果*檔名*找不到檔案， *pathname*包含空的 null 結尾字串。

*Pathname*緩衝區應該至少 **_MAX_PATH**適應建構的路徑名稱的完整長度的字元。 否則，請 **_searchenv**可能會溢位*pathname*緩衝並造成未預期的行為。

**_wsearchenv**是寬字元版本的 **_searchenv**，和引數 **_wsearchenv**是寬字元字串。 **_wsearchenv**並 **_searchenv**行為相同。

如果*檔名*為空字串，這些函式會傳回**ENOENT**。

如果*檔名*或是*pathname*是**NULL**指標，無效參數處理常式會叫用，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會傳回-1，並設定**errno**要**EINVAL**。

如需詳細資訊**errno**和錯誤碼，請參閱[errno 常數](../../c-runtime-library/errno-constants.md)。

在 C++ 中，這些函式具有多載樣板，可以叫用這些函式的更新、更安全之對應版本。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv**|**_searchenv**|**_searchenv**|**_wsearchenv**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_searchenv**|\<stdlib.h>|
|**_wsearchenv**|\<stdlib.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_searchenv.c
// compile with: /W3
// This program searches for a file in
// a directory that's specified by an environment variable.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char pathbuffer[_MAX_PATH];
   char searchfile[] = "CL.EXE";
   char envvar[] = "PATH";

   // Search for file in PATH environment variable:
   _searchenv( searchfile, envvar, pathbuffer ); // C4996
   // Note: _searchenv is deprecated; consider using _searchenv_s
   if( *pathbuffer != '\0' )
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );
   else
      printf( "%s not found\n", searchfile );
}
```

```Output
Path for CL.EXE:
C:\Program Files\Microsoft Visual Studio 8\VC\BIN\CL.EXE
```

## <a name="see-also"></a>另請參閱

[目錄控制](../../c-runtime-library/directory-control.md)<br/>
[getenv、_wgetenv](getenv-wgetenv.md)<br/>
[_putenv、_wputenv](putenv-wputenv.md)<br/>
[_searchenv_s、_wsearchenv_s](searchenv-s-wsearchenv-s.md)<br/>
