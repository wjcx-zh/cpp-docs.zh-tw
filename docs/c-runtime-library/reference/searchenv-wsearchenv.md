---
title: _searchenv、_wsearchenv
ms.date: 4/2/2020
api_name:
- _searchenv
- _wsearchenv
- _o__searchenv
- _o__wsearchenv
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 22a8ca8fa7e56a84289d7e90ffb519073f006b5c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332387"
---
# <a name="_searchenv-_wsearchenv"></a>_searchenv、_wsearchenv

使用環境路徑來搜尋檔案。 這些函式已有更安全的版本可供使用，請參閱 [_searchenv_s、_wsearchenv_s](searchenv-s-wsearchenv-s.md)。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

*檔案名稱*<br/>
要搜尋的檔案名稱。

*瓦爾名稱*<br/>
要搜尋的環境。

*路徑*<br/>
要儲存此完整路徑的緩衝區。

## <a name="remarks"></a>備註

**_searchenv**例程搜尋指定網域中的目標檔。 *varname*變數可以是指定目錄路徑列表的任何環境或使用者定義的變數,例如**PATH、LIB**或**INCLUDE。** **LIB** 由於 **_searchenv**區分大小寫 *,varname*應與環境變數的情況匹配。

此常式會先搜尋目前工作目錄中的檔案。 如果找不到此檔案，便會在環境變數指定的目錄中尋找。 如果目標檔案位於這些目錄中,則新創建的路徑將複製到*路徑名*中。 如果找不到*檔案名稱*檔案,*則路徑名稱*包含空 null 終止字串。

*路徑名稱*緩衝區應至少 **_MAX_PATH**個字元長,以適應構造路徑名稱的全長。 否則 **,_searchenv**可能會溢出*路徑名稱*緩衝區並導致意外行為。

**_wsearchenv**是 **_searchenv**的寬字元版本 **,_wsearchenv**的參數是寬字元字串。 **_wsearchenv**和 **_searchenv**行為相同。

如果*檔案名稱*是空字串,則這些函數將傳回**ENOENT**。

如果*檔案名*或*路徑名稱*是**NULL**指標,則呼叫無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許執行繼續,這些函數將傳回 -1 並將**errno**設定為**EINVAL**。

有關**errno**與錯誤代碼的詳細資訊,請參閱[errno 常量](../../c-runtime-library/errno-constants.md)。

在 C++ 中，這些函式具有多載樣板，可以叫用這些函式的更新、更安全之對應版本。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv**|**_searchenv**|**_searchenv**|**_wsearchenv**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_searchenv**|\<stdlib.h>|
|**_wsearchenv**|\<stdlib.h> 或 \<wchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

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
