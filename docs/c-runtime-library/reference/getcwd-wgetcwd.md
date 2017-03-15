---
title: "_getcwd、_wgetcwd | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wgetcwd"
  - "_getcwd"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_getcwd"
  - "wgetcwd"
  - "_wgetcwd"
  - "tgetcwd"
  - "_tgetcwd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "getcwd 函式"
  - "工作目錄"
  - "_wgetcwd 函式"
  - "_getcwd 函式"
  - "目前工作目錄"
  - "wgetcwd 函式"
  - "目錄 [c + +]，目前工作"
ms.assetid: 888dc8c6-5595-4071-be55-816b38e3e739
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _getcwd、_wgetcwd
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得目前工作目錄。  
  
## 語法  
  
```  
char *_getcwd(   
   char *buffer,  
   int maxlen   
);  
wchar_t *_wgetcwd(   
   wchar_t *buffer,  
   int maxlen   
);  
```  
  
#### 參數  
 `buffer`  
 路徑的儲存位置。  
  
 `maxlen`  
 路徑的最大長度 \(以字元為單位\)：`_getcwd` 為 `char`，`_wgetcwd` 為 `wchar_t`。  
  
## 傳回值  
 傳回 `buffer` 的指標。`NULL` 傳回值表示錯誤，且 `errno` 會設定為 `ENOMEM`，表示記憶體不足以配置 `maxlen` 個位元組 \(指定 `NULL` 引數給 `buffer` 時\)，或是設定為 `ERANGE`，表示路徑長度超過 `maxlen` 個字元。 如果 `maxlen` 小於或等於零，則這個函式會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  
  
 如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `_getcwd` 函式會取得預設磁碟機之目前工作目錄的完整路徑，並將其儲存在 `buffer`。 整數引數 `maxlen` 指定該路徑的最大長度。 如果路徑長度 \(包括結束的 null 字元\) 超過 `maxlen`，則會發生錯誤*。*`buffer` 引數可以是 `NULL`；系統會使用 `malloc` 自動配置大小至少為 `maxlen` 的緩衝區 \(並只在必要時才增加\) 來儲存路徑。 這個緩衝區稍後可以藉由呼叫 `free`，並對其傳遞 `_getcwd` 傳回值 \(已配置緩衝區的指標\) 來釋放。  
  
 `_getcwd` 會傳回代表目前工作目錄路徑的字串。 如果目前的工作目錄是根目錄，字串會以反斜線 \(`\`\) 結尾。 如果目前的工作目錄是根目錄以外的目錄，字串會以目錄名稱結尾，而不是反斜線。  
  
 `_wgetcwd` 是 `_getcwd` 的寬字元版本，`buffer` 引數與 `_wgetcwd` 的傳回值是寬字元字串。 否則，`_wgetcwd` 和 `_getcwd` 的行為即會相同。  
  
 定義 `_DEBUG` 和 `_CRTDBG_MAP_ALLOC` 之後，`_getcwd` 和 `_wgetcwd` 會由 `_getcwd_dbg` 和 `_wgetcwd_dbg` 的呼叫所取代，以便對記憶體配置進行偵錯。 如需詳細資訊，請參閱 [\_getcwd\_dbg、\_wgetcwd\_dbg](../../c-runtime-library/reference/getcwd-dbg-wgetcwd-dbg.md)。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tgetcwd`|`_getcwd`|`_getcwd`|`_wgetcwd`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_getcwd`|\<direct.h\>|  
|`_wgetcwd`|\<direct.h\> 或 \<wchar.h\>|  
  
 如需詳細的相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_getcwd.c  
// This program places the name of the current directory in the   
// buffer array, then displays the name of the current directory   
// on the screen. Passing NULL as the buffer forces getcwd to allocate  
// memory for the path, which allows the code to support file paths  
// longer than _MAX_PATH, which are supported by NTFS.  
  
#include <direct.h>  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char* buffer;  
  
   // Get the current working directory:   
   if( (buffer = _getcwd( NULL, 0 )) == NULL )  
      perror( "_getcwd error" );  
   else  
   {  
      printf( "%s \nLength: %d\n", buffer, strnlen(buffer) );  
      free(buffer);  
   }  
}  
```  
  
```Output  
C:\Code  
```  
  
## .NET Framework 對等用法  
 [System::Environment::CurrentDirectory](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)  
  
## 請參閱  
 [目錄控制](../../c-runtime-library/directory-control.md)   
 [\_chdir、\_wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [\_mkdir、\_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [\_rmdir、\_wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)