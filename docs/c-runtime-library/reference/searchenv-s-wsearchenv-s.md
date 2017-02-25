---
title: "_searchenv_s、_wsearchenv_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wsearchenv_s"
  - "_searchenv_s"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-environment-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_searchenv_s"
  - "_wsearchenv_s"
  - "wsearchenv_s"
  - "searchenv_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_searchenv_s 函式"
  - "_tsearchenv_s 函式"
  - "_wsearchenv_s 函式"
  - "緩衝區滿溢"
  - "緩衝區 [C++], 避免滿溢"
  - "緩衝區 [C++], 緩衝區滿溢"
  - "環境路徑"
  - "環境路徑, 搜尋檔案"
  - "檔案 [C++], 尋找"
  - "searchenv_s 函式"
  - "tsearchenv_s 函式"
  - "wsearchenv_s 函式"
ms.assetid: 47f9fc29-250e-4c09-b52e-9e9f0ef395ca
caps.latest.revision: 32
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 32
---
# _searchenv_s、_wsearchenv_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用環境路徑搜尋檔案。  這些 [\_searchenv, \_wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md) 版本有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
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
  
#### 參數  
 \[in\] `filename`  
 要搜尋的檔案名稱。  
  
 \[in\] `varname`  
 要搜尋的環境。  
  
 \[out\] `pathname`  
 儲存完整路徑的緩衝區。  
  
 \[in\] `numberOfElements`  
 `pathname`  緩衝區的大小。  
  
## 傳回值  
 如果成功，就是零，如果失敗，則為錯誤碼。  
  
 如果 `filename` 是空字串，，則傳回的值是 `ENOENT`。  
  
### 錯誤狀況  
  
|`filename`|`varname`|`pathname`|`numberOfElements`|傳回值|`pathname` 的內容|  
|----------------|---------------|----------------|------------------------|---------|--------------------|  
|any|any|`NULL`|any|`EINVAL`|N\/A|  
|`NULL`|any|any|any|`EINVAL`|沒變更|  
|any|any|any|\<\= 0|`EINVAL`|沒變更|  
  
 如果其中一個錯誤情況發生，無效的參數叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會將 `errno` 設定為 `EINVAL` 並傳回 `EINVAL`。  
  
## 備註  
 `_searchenv_s` 常式搜尋指定之網域的目標檔案。  `varname` 變數可以是指定目錄路徑清單，例如 `PATH`、 `LIB`和 `INCLUDE`的所有環境或使用者定義的變數。  因為 `_searchenv_s` 會區分大小寫， `varname` 應該與環境變數的情況相符。  如果 `varname` 不符合流程的環境中定義的環境變數的名稱，則函式會傳回零，而 `pathname` 變數保持不變。  
  
 常式會先搜尋目前工作目錄中的檔案。  如果找不到檔案，它會透過指定的環境變數尋找下一個目錄。  如果目標檔案在這些目錄的其中一種，新建立的路徑複製到 `pathname`。  如果 `filename` 檔案沒找到， `pathname` 會包含空的 NULL 結尾字串。  
  
 `pathname` 緩衝區應該有符合至少 `_MAX_PATH` 完整長度字元建構的路徑名稱。  否則 `_searchenv_s` 可能滿溢 `pathname` 緩衝區造成未預期的行為。  
  
 `_wsearchenv_s` 是 `_searchenv_s` 的寬字元版本，`_wsearchenv_s` 的引數是寬字元字串。  `_wsearchenv_s` 和 `_searchenv_s` 其餘行為相同。  
  
 C\+\+ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_tsearchenv_s`|`_searchenv_s`|`_searchenv_s`|`_wsearchenv_s`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_searchenv_s`|\<stdlib.h\>|  
|`_wsearchenv_s`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
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
  
  **CL.EXE 的路徑:**  
**C:\\Program Files\\Microsoft Visual Studio 2010\\VC\\BIN\\CL.EXE**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [目錄控制](../../c-runtime-library/directory-control.md)   
 [\_searchenv、\_wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)   
 [getenv、\_wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [\_putenv、\_wputenv](../../c-runtime-library/reference/putenv-wputenv.md)