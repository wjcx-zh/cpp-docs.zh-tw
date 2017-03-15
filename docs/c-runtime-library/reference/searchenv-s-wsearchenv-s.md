---
title: "_searchenv_s、_wsearchenv_s | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 32
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
ms.openlocfilehash: c70908d3c884eed962560e0a5284c66c3c234a7e
ms.lasthandoff: 02/24/2017

---
# <a name="searchenvs-wsearchenvs"></a>_searchenv_s、_wsearchenv_s
使用環境路徑來搜尋檔案。 這些版本的 [_searchenv、_wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md) 具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。  
  
> [!IMPORTANT]
>  這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 [in] `filename`  
 要搜尋的檔案名稱。  
  
 [in] `varname`  
 要搜尋的環境。  
  
 [輸出] `pathname`  
 要儲存此完整路徑的緩衝區。  
  
 [in] `numberOfElements`  
 `pathname` 緩衝區的大小。  
  
## <a name="return-value"></a>傳回值  
 如果成功，就是零，如果失敗，則為錯誤碼。  
  
 如果 `filename` 是空字串，則傳回值是 `ENOENT`。  
  
### <a name="error-conditions"></a>錯誤狀況  
  
|`filename`|`varname`|`pathname`|`numberOfElements`|傳回值|`pathname` 的內容。|  
|----------------|---------------|----------------|------------------------|------------------|----------------------------|  
|any|任何|`NULL`|any|`EINVAL`|N/A|  
|`NULL`|任何|任何|任何|`EINVAL`|未變更|  
|any|任何|any|<= 0|`EINVAL`|未變更|  
  
 如果發生上述任何錯誤狀況，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 `EINVAL`。  
  
## <a name="remarks"></a>備註  
 `_searchenv_s` 常式會搜尋指定網域中的目標檔案。 `varname` 變數可以是指定目錄路徑清單的任何環境或使用者定義變數，例如 `PATH`、`LIB` 和 `INCLUDE`。 因為 `_searchenv_s` 會區分大小寫，所以 `varname` 應該要與環境變數的大小寫相符。 如果 `varname` 不符合處理序環境中所定義環境變數的名稱，此函式會傳回零，而且 `pathname` 變數不會變更。  
  
 此常式會先搜尋目前工作目錄中的檔案。 如果找不到此檔案，接著會在環境變數指定的目錄中尋找。 如果目標檔案在這些目錄其中之一，則會將新建立的路徑複製到 `pathname`。 如果找不到 `filename` 檔案，則 `pathname` 會包含空的 null 結尾字串。  
  
 `pathname` 緩衝區應該要有至少 `_MAX_PATH` 字元的長度，藉此容納全部長度的建構路徑名稱。 否則，`_searchenv_s` 可能會讓 `pathname` 緩衝區滿溢，並造成未預期的行為。  
  
 `_wsearchenv_s` 是 `_searchenv_s` 的寬字元版本；`_wsearchenv_s` 的引數是寬字元字串。 否則，`_wsearchenv_s` 和 `_searchenv_s` 的行為即會相同。  
  
 C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tsearchenv_s`|`_searchenv_s`|`_searchenv_s`|`_wsearchenv_s`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_searchenv_s`|\<stdlib.h>|  
|`_wsearchenv_s`|\<stdlib.h> 或 \<wchar.h>|  
  
 如需相容性詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
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
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [目錄控制](../../c-runtime-library/directory-control.md)   
 [_searchenv、_wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)   
 [getenv、_wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [_putenv、_wputenv](../../c-runtime-library/reference/putenv-wputenv.md)
