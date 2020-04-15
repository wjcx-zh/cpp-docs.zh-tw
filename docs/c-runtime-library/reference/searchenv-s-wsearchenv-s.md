---
title: _searchenv_s、_wsearchenv_s
ms.date: 4/2/2020
api_name:
- _wsearchenv_s
- _searchenv_s
- _o__searchenv_s
- _o__wsearchenv_s
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
- _searchenv_s
- _wsearchenv_s
- wsearchenv_s
- searchenv_s
helpviewer_keywords:
- tsearchenv_s function
- files [C++], finding
- buffers [C++], buffer overruns
- environment paths, searching for files
- wsearchenv_s function
- searchenv_s function
- _tsearchenv_s function
- buffer overruns
- buffers [C++], avoiding overruns
- _wsearchenv_s function
- _searchenv_s function
- environment paths
ms.assetid: 47f9fc29-250e-4c09-b52e-9e9f0ef395ca
ms.openlocfilehash: 3d526c546e1496b3b13b14a12c9025cbd0347cd2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332405"
---
# <a name="_searchenv_s-_wsearchenv_s"></a>_searchenv_s、_wsearchenv_s

使用環境路徑來搜尋檔案。 這些版本的 [_searchenv、_wsearchenv](searchenv-wsearchenv.md) 具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
errno_t _searchenv_s(
   const char *filename,
   const char *varname,
   char *pathname,
   size_t numberOfElements
);
errno_t _wsearchenv_s(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t *pathname,
   size_t numberOfElements
);
template <size_t size>
errno_t _searchenv_s(
   const char *filename,
   const char *varname,
   char (&pathname)[size]
); // C++ only
template <size_t size>
errno_t _wsearchenv_s(
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

*元素數*<br/>
*路徑名稱*緩衝區的大小。

## <a name="return-value"></a>傳回值

如果成功，就是零，如果失敗，則為錯誤碼。

如果*檔案名稱*是空字串,則傳回值為**ENOENT**。

### <a name="error-conditions"></a>錯誤狀況

|*檔案名稱*|*瓦爾名稱*|*路徑*|*元素數*|傳回值|*路徑名稱*的內容|
|----------------|---------------|----------------|------------------------|------------------|----------------------------|
|任意|任意|**空**|任意|**埃因瓦爾**|n/a|
|**空**|任意|任意|任意|**埃因瓦爾**|未變更|
|任意|任意|任意|<= 0|**埃因瓦爾**|未變更|

如果發生上述任何錯誤狀況，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許執行繼續,這些函數將**errno**設定為**EINVAL**並傳回**EINVAL**。

## <a name="remarks"></a>備註

**_searchenv_s**例程搜索指定網域中的目標檔。 *varname*變數可以是指定目錄路徑列表的任何環境或使用者定義的變數,如**PATH、LIB****PATH**和**INCLUDE**。 由於 **_searchenv_s**區分大小寫 *,varname*應與環境變數的情況匹配。 如果*varname*與行程環境中定義的環境變數的名稱不匹配,則該變數傳回零,*路徑名稱*變數保持不變。

此常式會先搜尋目前工作目錄中的檔案。 如果找不到此檔案，接著會在環境變數指定的目錄中尋找。 如果目標檔案位於這些目錄中,則新創建的路徑將複製到*路徑名*中。 如果找不到*檔案名稱*檔案,*則路徑名稱*包含空 null 終止字串。

*路徑名稱*緩衝區應至少 **_MAX_PATH**個字元長,以適應構造路徑名稱的全長。 否則 **,_searchenv_s**可能會溢出*路徑名稱*緩衝區,從而導致意外行為。

**_wsearchenv_s**是 **_searchenv_s**的寬字元版本;要 **_wsearchenv_s**的參數是寬字元字串。 **_wsearchenv_s**和 **_searchenv_s**行為相同。

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv_s**|**_searchenv_s**|**_searchenv_s**|**_wsearchenv_s**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_searchenv_s**|\<stdlib.h>|
|**_wsearchenv_s**|\<stdlib.h> 或 \<wchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_searchenv_s.c
/* This program searches for a file in
* a directory specified by an environment variable.
*/

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char pathbuffer[_MAX_PATH];
   char searchfile[] = "CL.EXE";
   char envvar[] = "PATH";
   errno_t err;

   /* Search for file in PATH environment variable: */
   err = _searchenv_s( searchfile, envvar, pathbuffer, _MAX_PATH );
   if (err != 0)
   {
      printf("Error searching the path. Error code: %d\n", err);
   }
   if( *pathbuffer != '\0' )
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );
   else
      printf( "%s not found\n", searchfile );
}
```

```Output
Path for CL.EXE:
C:\Program Files\Microsoft Visual Studio 2010\VC\BIN\CL.EXE
```

## <a name="see-also"></a>另請參閱

[目錄控制](../../c-runtime-library/directory-control.md)<br/>
[_searchenv、_wsearchenv](searchenv-wsearchenv.md)<br/>
[getenv、_wgetenv](getenv-wgetenv.md)<br/>
[_putenv、_wputenv](putenv-wputenv.md)<br/>
