---
title: "_searchenv、_wsearchenv | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs:
- C++
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
caps.latest.revision: 33
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 3370ea3fcad8874fe9bdcd737d2488509f740fd6
ms.lasthandoff: 02/24/2017

---
# <a name="searchenv-wsearchenv"></a>_searchenv、_wsearchenv
使用環境路徑來搜尋檔案。 這些函式已有更安全的版本可供使用，請參閱 [_searchenv_s、_wsearchenv_s](../../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `filename`  
 要搜尋的檔案名稱。  
  
 `varname`  
 要搜尋的環境。  
  
 `pathname`  
 要儲存此完整路徑的緩衝區。  
  
## <a name="remarks"></a>備註  
 `_searchenv` 常式會搜尋指定網域中的目標檔案。 `varname` 變數可以是指定目錄路徑清單之任何環境或使用者定義的變數，例如 `PATH`、`LIB` 或 `INCLUDE`。 因為 `_searchenv` 會區分大小寫，所以 `varname` 應該要與環境變數的大小寫相符。  
  
 此常式會先搜尋目前工作目錄中的檔案。 如果找不到此檔案，便會在環境變數指定的目錄中尋找。 如果目標檔案在這些目錄其中之一，則會將新建立的路徑複製到 `pathname`。 如果找不到 `filename` 檔案，則 `pathname` 會包含空的 null 結尾字串。  
  
 `pathname` 緩衝區應該要有至少 `_MAX_PATH` 字元的長度，藉此容納全部長度的建構路徑名稱。 否則，`_searchenv` 可能讓 `pathname` 緩衝區滿溢，並造成未預期的行為。  
  
 `_wsearchenv` 是 `_searchenv` 的寬字元版本；而 `_wsearchenv` 的引數是寬字元字串。 否則，`_wsearchenv` 和 `_searchenv` 的行為即會相同。  
  
 如果 `filename` 是空字串，則這些函式會傳回 `ENOENT`。  
  
 如果 `filename` 或 `pathname` 為 `NULL` 指標，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回 -1，並將 `errno` 設為 `EINVAL`。  
  
 如需 `errno` 和錯誤碼的詳細資訊，請參閱 [errno 常數](../../c-runtime-library/errno-constants.md)。  
  
 在 C++ 中，這些函式具有多載樣板，可以叫用這些函式的更新、更安全之對應版本。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tsearchenv`|`_searchenv`|`_searchenv`|`_wsearchenv`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_searchenv`|\<stdlib.h>|  
|`_wsearchenv`|\<stdlib.h> 或 \<wchar.h>|  
  
 如需相容性詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
  
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
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [目錄控制](../../c-runtime-library/directory-control.md)   
 [getenv、_wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [_putenv、_wputenv](../../c-runtime-library/reference/putenv-wputenv.md)   
 [_searchenv_s、_wsearchenv_s](../../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)
