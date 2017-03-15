---
title: "_fullpath、_wfullpath | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fullpath"
  - "_wfullpath"
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
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wfullpath"
  - "fullpath"
  - "_wfullpath"
  - "_fullpath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fullpath 函式"
  - "_wfullpath 函式"
  - "絕對路徑"
  - "fullpath 函式"
  - "相對檔案路徑"
  - "wfullpath 函式"
ms.assetid: 4161ec17-0d22-45dd-b07d-0222553afae9
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _fullpath、_wfullpath
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立絕對或完整路徑名稱指定的相對路徑名稱。  
  
## 語法  
  
```  
char *_fullpath(   
   char *absPath,  
   const char *relPath,  
   size_t maxLength   
);  
wchar_t *_wfullpath(   
   wchar_t *absPath,  
   const wchar_t *relPath,  
   size_t maxLength   
);  
```  
  
#### 參數  
 `absPath`  
 out 包含絕對或完整路徑名稱的緩衝區的指標或 NULL。  
  
 `relPath`  
 相對路徑名稱。  
  
 `maxLength`  
 絕對路徑名稱緩衝區 \(`absPath`\) 的最大長度。  此長度可以在 `_fullpath` 中的位元組，但是在寬字元 \(`wchar_t`\) 的 `_wfullpath`。  
  
## 傳回值  
 這些函式都會傳回指標包含絕對路徑名稱 \(`absPath`\) 的緩衝區。  如果發生錯誤 \(例如，因此，如果在 `relPath` 中傳遞的值包含無效或找不到的磁碟機代號，或者，如果建立的絕對路徑名稱 \(`absPath`\) 的長度大於 `maxLength`\) 函式會傳回 `NULL`。  
  
## 備註  
 `_fullpath` 函式。 `absPath`展開 `relPath` 的相對路徑名稱到其完整或絕對路徑並儲存此名稱*。*如果 `absPath` 是空的，則`malloc` 用來配置足夠的長度緩衝區保存路徑名稱。  為呼叫端的責任釋放這個緩衝區。  相對路徑名稱指定路徑從目前位置的其他位置 \(例如目前工作目錄:"."\)。  絕對路徑名稱是陳述式需要的整個路徑達到從檔案系統的根的預期位置相對路徑名稱的擴充。  不同於 `_makepath`， `_fullpath` 可以用來取得絕對路徑名稱對於相對路徑 \(`relPath`\) 中包含".\/" 或 "..\/" 的名稱。  
  
 例如，使用 C 執行階段常式，應用程式必須包含常式宣告的標頭檔。  每個標頭檔包含陳述式參考檔案的位置以相對方式 \(從應用程式的工作目錄\):  
  
```  
#include <stdlib.h>  
```  
  
 當絕對路徑 \(實際的檔案系統位置\) 檔案可能是:  
  
```  
\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h  
```  
  
 `_fullpath` 適時地自動處理多位元組字元的字串參數，根據目前使用的多位元組字碼頁來辨認多位元組字元序列。  `_wfullpath`  是 `_fullpath` 的寬字元版本，字串引數的`_wfullpath`  是寬字元字串。  `_wfullpath`  和 `_fullpath`  行為相同，除了 `_wfullpath`  不處理多位元組字元字串。  
  
 如果 `_DEBUG`  和 `_CRTDBG_MAP_ALLOC`  都被定義時，呼叫 `_fullpath` 和 `_wfullpath` 是由 `_fullpath_dbg` 和 `_wfullpath_dbg` 的呼叫取代允許偵錯記憶體配置。  如需詳細資訊，請參閱 [\_fullpath\_dbg， \_wfullpath\_dbg](../../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md)。  
  
 如果 [參數驗證](../../c-runtime-library/parameter-validation.md) 小於或等於零，則這個函式會叫用無效的參數處理常式，如 `maxlen`中所述。  如果允許繼續執行，函式將 `errno` 設置為 `EINVAL` 並回傳 `NULL` 。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------|----------------|-------------------|  
|`_tfullpath`|`_fullpath`|`_fullpath`|`_wfullpath`|  
  
 如果 `absPath` 緩衝區是 `NULL`， `_fullpath` 呼叫 [malloc](../../c-runtime-library/reference/malloc.md) 配置緩衝區並忽略 `maxLength` 引數。  為呼叫端的責任解除這個緩衝區 \(使用 [free](../../c-runtime-library/reference/free.md)\) 屬性。  如果 `relPath` 引數指定驅動程式，則這個磁碟機目前目錄結合路徑。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`_fullpath`|\<stdlib.h\>|  
|`_wfullpath`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_fullpath.c  
// This program demonstrates how _fullpath  
// creates a full path from a partial path.  
  
#include <stdio.h>  
#include <conio.h>  
#include <stdlib.h>  
#include <direct.h>  
  
void PrintFullPath( char * partialPath )  
{  
   char full[_MAX_PATH];  
   if( _fullpath( full, partialPath, _MAX_PATH ) != NULL )  
      printf( "Full path is: %s\n", full );  
   else  
      printf( "Invalid path\n" );  
}  
  
int main( void )  
{  
   PrintFullPath( "test" );  
   PrintFullPath( "\\test" );  
   PrintFullPath( "..\\test" );  
}  
```  
  
  **完整路徑為:C:\\Documents and Settings\\user\\My Documents \\test**  
**完整路徑為:C:\\test**  
**完整路徑為:C:\\Documents and Settings\\user\\test**   
## .NET Framework 對等用法  
 [System::IO::File::Create](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [\_getcwd、\_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [\_getdcwd、\_wgetdcwd](../../c-runtime-library/reference/getdcwd-wgetdcwd.md)   
 [\_makepath、\_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [\_splitpath、\_wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)