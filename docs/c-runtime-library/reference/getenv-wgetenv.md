---
title: "getenv、_wgetenv | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "getenv"
  - "_wgetenv"
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
  - "_wgetenv"
  - "getenv"
  - "_tgetenv"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tgetenv 函式"
  - "_wgetenv 函式"
  - "環境值"
  - "環境變數"
  - "getenv 函式"
  - "tgetenv 函式"
  - "wgetenv 函式"
ms.assetid: 3b9cb9ab-a126-4e0e-a44f-6c5a7134daf4
caps.latest.revision: 31
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# getenv、_wgetenv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從目前環境取得值。  更多這些函式的可用安全版本，請參閱 [getenv\_s、\_wgetenv\_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md)。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
char *getenv(   
   const char *varname   
);  
wchar_t *_wgetenv(   
   const wchar_t *varname   
);  
```  
  
#### 參數  
 `varname`  
 環境變數名稱。  
  
## 傳回值  
 將指標傳回包含 `varname`的環境表格項目。  使用傳回的指標修改環境變數的值是不安全的。  使用 `_putenv` 函式來修改環境變數的值。  在環境表格中找不到 `varname` ，則傳回 `NULL` 。  
  
## 備註  
 `getenv` 函式會搜尋環境變數名稱的 `varname`。  Windows 作業系統中 `getenv` 不區分大小寫 。  `getenv` 和 `_putenv` 使用環境指向由全域變數 `_environ` 的複本存取環境。  `getenv` 只能使用在資料結構可供這個執行階段程式庫和由作業系統不在環境「為處理序」建立的區段時使用。  因此，使用 `envp` 引數傳遞至 [main](../../cpp/main-program-startup.md) 或 [wmain](../../cpp/main-program-startup.md) 的程式可能會擷取不正確的資訊。  
  
 如果 `varname` 為 `NULL`，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，函式將 `errno` 設置為 `EINVAL` 並回傳 `NULL` 。  
  
 `_wgetenv` 是 `getenv` 的寬字元版本，`_wgetenv` 函式的參數和回傳值是寬字元字串。  `_wenviron` 全域變數是 `_environ`寬字元版本。  
  
 在 MBCS 程式 \(例如，在 SBCS ASCII\)， `_wenviron` 最初是 `NULL` 因為環境由多位元組字元字串所組成。  接下來，第一次呼叫 `_wputenv`，或者如果 MBCS 環境已經存在時，則在第一次呼叫 `_wgetenv` ，會建立對應的寬字元字串環境且被 `_wenviron` 指向。  
  
 同樣在 Unicode \(`_wmain`\) 程式， `_environ` 最初是 `NULL` ，因為環境由寬字元字串所組成。  接下來，第一次呼叫 `_putenv`，或者如果 MBCS 環境已經存在時，則在第一次呼叫 `getenv` ，會建立對應的寬字元字串環境且被 `_environ` 指向。  
  
 當兩個環境複本 \(MBCS 和 Unicode\) 時同時存在的程式，這個執行階段系統必須維護兩份複本，造成較慢的執行時間。  例如，當您呼叫 `_putenv`，一個呼叫 `_wputenv` 的方式也會自動執行，因此，這兩個環境字串對應。  
  
> [!CAUTION]
>  在極少的情況下，當這個 Runtime 系統維護的 Unicode 版本和環境的多位元組版本時，這兩個環境版本可能對應不正確。  這是因為雖然任何唯一的多位元組字元字串對應到唯一的 Unicode 字串，從唯一的 Unicode 字串對應到多位元組字元字串不一定是唯一的。  如需詳細資訊，請參閱 [\_environ, \_wenviron](../../c-runtime-library/environ-wenviron.md)。  
  
> [!NOTE]
>  `_putenv` 和 `_getenv` 函式群不是安全執行緒。  當 `_putenv` 修改字串時產生隨機失敗，`_getenv` 會傳回字串指標。  確定這些函式的呼叫已同步。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tgetenv`|`getenv`|`getenv`|`_wgetenv`|  
  
 需要檢查或變更 `TZ` 環境變數，可使用 `getenv`， `_putenv` 和 `_tzset` 。  如需 `TZ`的詳細資訊，請參閱 [\_tzset](../../c-runtime-library/reference/tzset.md) 和 [\_daylight、時區和 \_tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`getenv`|\<stdlib.h\>|  
|`_wgetenv`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_getenv.c  
// compile with: /W3  
// This program uses getenv to retrieve  
// the LIB environment variable and then uses  
// _putenv to change it to a new value.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char *libvar;  
  
   // Get the value of the LIB environment variable.  
   libvar = getenv( "LIB" ); // C4996  
   // Note: getenv is deprecated; consider using getenv_s instead  
  
   if( libvar != NULL )  
      printf( "Original LIB variable is: %s\n", libvar );  
  
   // Attempt to change path. Note that this only affects the environment  
   // variable of the current process. The command processor's  
   // environment is not changed.  
   _putenv( "LIB=c:\\mylib;c:\\yourlib" ); // C4996  
   // Note: _putenv is deprecated; consider using putenv_s instead  
  
   // Get new value.  
   libvar = getenv( "LIB" ); // C4996  
  
   if( libvar != NULL )  
      printf( "New LIB variable is: %s\n", libvar );  
}  
```  
  
  **原始的 LIB 變數是: C:\\progra~1\\devstu~1\\vc\\lib**  
**新的 LIB 變數是: c:\\mylib; c:\\yourlib**   
## .NET Framework 對等用法  
 [System::Environment::GetEnvironmentVariable](https://msdn.microsoft.com/en-us/library/system.environment.getenvironmentvariable.aspx)  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [\_putenv、\_wputenv](../../c-runtime-library/reference/putenv-wputenv.md)   
 [環境常數](../../c-runtime-library/environmental-constants.md)