---
title: "perror、_wperror | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wperror"
  - "perror"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_wperror"
  - "_tperror"
  - "perror"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tperror 函式"
  - "_wperror 函式"
  - "錯誤訊息, 列印"
  - "perror 函式"
  - "列印錯誤訊息"
  - "tperror 函式"
  - "wperror 函式"
ms.assetid: 34fce792-16fd-4673-9849-cd88b54b6cd5
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# perror、_wperror
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

列印錯誤訊息。  
  
## 語法  
  
```  
  
      void perror(  
   const char *string   
);  
void _wperror(  
   const wchar_t *string   
);  
```  
  
#### 參數  
 `string`  
 欲列印的字串訊息。  
  
## 備註  
 `perror` 函式會列印錯誤訊息至 `stderr`。  `_wperror` 是 **\_perror** 的寬字元版本； `_wperror` 的 `string` 引數是寬字元字串。  此外 `_wperror` 和 **\_perror** 的行為相同。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tperror`|`perror`|`perror`|`_wperror`|  
  
 `string` 會先列印，後面加上冒號，然後由造成錯誤的最後一個程式庫呼叫的系統錯誤訊息和最後的新行字元。  如果 `string` 為 null 指標或指標為空字串， `perror` 只列印系統錯誤訊息。  
  
 錯誤代碼儲存在變數 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 中 \(定義在 ERRNO.H\)。  系統錯誤訊息透過變數 [\_sys\_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 存取，此變數為依錯誤代碼排序的訊息陣列。  `perror` 列印適當的錯誤訊息會使用 `errno` 值做為對 `_sys_errlist` 的索引。  [\_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 變數的值定義為項目 `_sys_errlist` 陣列中的最大數目。  
  
 若要產生正確的結果，請在程式庫常式傳回錯誤之後立刻呼叫 `perror`。  否則，後續呼叫可以覆寫 `errno` 值。  
  
 在 Windows 作業系統，在 ERRNO.H 清單的 `errno` 值未使用。  這些值是保留給 UNIX 作業系統使用的。  如需提供 Windows 作業系統使用的 `errno` 值的清單，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 作業系統。  `perror` 列印這些平台未使用的所有 `errno` 值為空字串。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`perror`|\<stdio.h\> or \<stdlib.h\>|  
|`_wperror`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_perror.c  
// compile with: /W3  
/* This program attempts to open a file named  
 * NOSUCHF.ILE. Because this file probably doesn't exist,  
 * an error message is displayed. The same message is  
 * created using perror, strerror, and _strerror.  
 */  
  
#include <fcntl.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <io.h>  
#include <stdlib.h>  
#include <stdio.h>  
#include <string.h>  
#include <share.h>  
  
int main( void )  
{  
   int  fh;  
  
   if( _sopen_s( &fh, "NOSUCHF.ILE", _O_RDONLY, _SH_DENYNO, 0 ) != 0 )  
   {  
      /* Three ways to create error message: */  
      perror( "perror says open failed" );  
      printf( "strerror says open failed: %s\n",  
         strerror( errno ) ); // C4996  
      printf( _strerror( "_strerror says open failed" ) ); // C4996  
      // Note: strerror and _strerror are deprecated; consider  
      // using strerror_s and _strerror_s instead.  
   }  
   else  
   {  
      printf( "open succeeded on input file\n" );  
      _close( fh );  
   }  
}  
```  
  
## Output  
  
```  
perror says open failed: No such file or directory  
strerror says open failed: No such file or directory  
_strerror says open failed: No such file or directory  
```  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [strerror、\_strerror、\_wcserror、\_\_wcserror](../../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)