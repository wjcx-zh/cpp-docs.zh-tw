---
title: "_dupenv_s、_wdupenv_s | Microsoft Docs"
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
  - "_dupenv_s"
  - "_wdupenv_s"
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
  - "tdupenv_s"
  - "_dupenv_s"
  - "wdupenv_s"
  - "dupenv_s"
  - "_tdupenv_s"
  - "_wdupenv_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_dupenv_s 函式"
  - "_tdupenv_s 函式"
  - "_wdupenv_s 函式"
  - "dupenv_s 函式"
  - "環境變數"
  - "tdupenv_s 函式"
  - "wdupenv_s 函式"
ms.assetid: b729ecc2-a31d-4ccf-92a7-5accedb8f8c8
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _dupenv_s、_wdupenv_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從目前的環境取得值。  
  
> [!IMPORTANT]
>  這個 API 不能用於在 Windows 執行階段中執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
errno_t _dupenv_s(    char **buffer,    size_t *numberOfElements,    const char *varname ); errno_t _wdupenv_s(    wchar_t **buffer,    size_t *numberOfElements,    const wchar_t *varname );  
```  
  
#### 參數  
 `buffer`  
 要儲存變數的值的緩衝區。  
  
 `numberOfElements`  
 `buffer` 的大小。  
  
 `varname`  
 環境變數名稱。  
  
## 傳回值  
 若成功，就是零；若失敗，則為錯誤碼。  
  
 這些函式會驗證其參數；若 `buffer` 或 `varname` 為 `NULL`，會叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  若允許繼續執行，函式會將 `errno` 設定為 `EINVAL` 並傳回 `EINVAL`。  
  
 若這些函是無法配置足夠的記憶體，會將 `buffer` 設定為 `NULL`，將 `numberOfElements` 設定為 0，並傳回 `ENOMEM`。  
  
## 備註  
 `_dupenv_s` 函式會在環境變數清單中搜尋 `varname`。  若找到變數，`_dupenv_s` 會配置緩衝區，並將變數的值複製到緩衝區中。  會在 `buffer` 和 `numberOfElements` 中傳回緩衝區的位址和長度。  `_dupenv_s` 可透過配置緩衝區本身提供比 [getenv\_s、\_wgetenv\_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md) 更方便的選擇。  
  
> [!NOTE]
>  其會呼叫程式的責任藉由呼叫 [free](../../c-runtime-library/reference/free.md) 釋放記憶體。  
  
 若找不到變數，`buffer` 會設為 `NULL`，`numberOfElements` 則設為 0，且傳回值為 0，因為此情況不會被認為是錯誤狀況。  
  
 若您不需要緩衝區的大小，可以忽略 `numberOfElements` 的 `NULL`。  
  
 `_dupenv_s` 在 Windows 作業系統中不區分大小寫。  `_dupenv_s` 會使用全域變數 `_environ` 所指出的環境複本來存取環境。  如需 `_environ` 的討論，請參閱 [getenv\_s、\_wgetenv\_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md) 中的「備註」。  
  
 `buffer` 中的值是環境變數之值的複本，對其進行修改不會對環境產生任何影響。  使用 [\_putenv\_s、\_wputenv\_s](../../c-runtime-library/reference/putenv-s-wputenv-s.md) 函式修改環境變數的值。  
  
 `_wdupenv_s` 是寬字元版本的 `_dupenv_s`；`_wdupenv_s` 的引數是寬字元字串。  `_wenviron` 全域變數是寬字元版本的 `_environ`。  如需 `_wenviron` 的詳細資訊，請參閱 [getenv\_s、\_wgetenv\_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md) 中的「備註」。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tdupenv_s`|`_dupenv_s`|`_dupenv_s`|`_wdupenv_s`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_dupenv_s`|\<stdlib.h\>|  
|`_wdupenv_s`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_dupenv_s.c  
#include  <stdlib.h>  
  
int main( void )  
{  
   char *pValue;  
   size_t len;  
   errno_t err = _dupenv_s( &pValue, &len, "pathext" );  
   if ( err ) return -1;  
   printf( "pathext = %s\n", pValue );  
   free( pValue );  
   err = _dupenv_s( &pValue, &len, "nonexistentvariable" );  
   if ( err ) return -1;  
   printf( "nonexistentvariable = %s\n", pValue );  
   free( pValue ); // It's OK to call free with NULL  
}  
```  
  
## 範例輸出  
  
```  
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl  
nonexistentvariable = (null)  
```  
  
## .NET Framework 對等用法  
 [System::Environment::GetEnvironmentVariable](https://msdn.microsoft.com/en-us/library/system.environment.getenvironmentvariable.aspx)  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [環境常數](../../c-runtime-library/environmental-constants.md)   
 [\_dupenv\_s\_dbg、\_wdupenv\_s\_dbg](../../c-runtime-library/reference/dupenv-s-dbg-wdupenv-s-dbg.md)   
 [getenv\_s、\_wgetenv\_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md)   
 [\_putenv\_s、\_wputenv\_s](../../c-runtime-library/reference/putenv-s-wputenv-s.md)