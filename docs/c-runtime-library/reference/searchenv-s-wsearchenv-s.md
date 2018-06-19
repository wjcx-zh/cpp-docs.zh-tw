---
title: _searchenv_s、_wsearchenv_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wsearchenv_s
- _searchenv_s
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
- _searchenv_s
- _wsearchenv_s
- wsearchenv_s
- searchenv_s
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b14dee908cdf1cc0d564047035a72f501df130b4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32410911"
---
# <a name="searchenvs-wsearchenvs"></a>_searchenv_s、_wsearchenv_s

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

*filename*<br/>
要搜尋的檔案名稱。

*varname*<br/>
要搜尋的環境。

*路徑名稱*<br/>
要儲存此完整路徑的緩衝區。

*numberOfElements*<br/>
大小*pathname*緩衝區。

## <a name="return-value"></a>傳回值

如果成功，就是零，如果失敗，則為錯誤碼。

如果*filename*為空字串，則傳回值是**ENOENT**。

### <a name="error-conditions"></a>錯誤狀況

|*filename*|*varname*|*路徑名稱*|*numberOfElements*|傳回值|內容*路徑名稱*|
|----------------|---------------|----------------|------------------------|------------------|----------------------------|
|任何|任何|**NULL**|任何|**EINVAL**|N/A|
|**NULL**|任何|任何|任何|**EINVAL**|未變更|
|任何|任何|任何|<= 0|**EINVAL**|未變更|

如果發生上述任何錯誤狀況，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將**errno**至**EINVAL**並傳回**EINVAL**。

## <a name="remarks"></a>備註

**_Searchenv_s**例行搜尋指定的網域中的目標檔案。 *Varname*變數可以是任何環境或使用者定義的變數，例如指定的目錄路徑清單**路徑**， **LIB**，和**INCLUDE**. 因為 **_searchenv_s**區分大小寫， *varname*應該與環境變數的大小寫。 如果*varname*不的符合處理序的環境中定義的環境變數的名稱，此函式會傳回零和*pathname*變數是不變。

此常式會先搜尋目前工作目錄中的檔案。 如果找不到此檔案，接著會在環境變數指定的目錄中尋找。 如果目標檔案，其中一個這些目錄中新建立的路徑會複製到*pathname*。 如果*filename*找不到檔案， *pathname*包含空的 null 結尾字串。

*Pathname*緩衝區應該要有至少 **_MAX_PATH**字元的長度，藉此容納完整長度的建構的路徑名稱。 否則， **_searchenv_s**可能滿溢*pathname*緩衝區導致未預期的行為。

**_wsearchenv_s**是寬字元版本的 **_searchenv_s**; 的引數 **_wsearchenv_s**是寬字元字串。 **_wsearchenv_s**和 **_searchenv_s**除此之外的行為相同。

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv_s**|**_searchenv_s**|**_searchenv_s**|**_wsearchenv_s**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_searchenv_s**|\<stdlib.h>|
|**_wsearchenv_s**|\<stdlib.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
