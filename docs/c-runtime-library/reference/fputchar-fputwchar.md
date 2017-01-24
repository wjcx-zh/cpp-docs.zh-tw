---
title: "_fputchar、_fputwchar | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fputchar"
  - "_fputwchar"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "fputtchar"
  - "_fputwchar"
  - "fputwchar"
  - "_fputtchar"
  - "fputchar"
  - "_fputchar"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fputchar 函式"
  - "_fputtchar 函式"
  - "_fputwchar 函式"
  - "fputchar 函式"
  - "fputtchar 函式"
  - "fputwchar 函式"
  - "標準輸出, 寫入至"
ms.assetid: b92ff600-a924-4f2b-b0e7-3097ee31bdff
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fputchar、_fputwchar
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將字元寫入 `stdout`。  
  
## 語法  
  
```  
int _fputchar(  
   int c   
);  
wint_t _fputwchar(  
   wchar_t c   
);  
```  
  
#### 參數  
 `c`  
 待寫入字元。  
  
## 傳回值  
 這些函式都會傳回寫入的字元。  對於`_fputchar`, 回傳值為 `EOF` 則表示錯誤。  對於`_fputwchar`, 回傳值為 `WEOF` 則表示錯誤。  如果 c 為 `NULL`，這些函式會產生不正確的參數例外狀況，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，它們會傳回 `EOF` 或 `WEOF`，並將 `errno` 設定為`EINVAL`。  
  
 如需有關這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 這兩個函式給 `stdout` 寫入單一字元 `c` 並按照指示器屬性。  `_fputchar` 相當於 `fputc(``stdout )`。  它也相當於 `putchar`，不過，只有會實作為函式，而不是函式和巨集。  不同於 `fputc` 和 `putchar`，這些函式與 ANSI 標準。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_fputtchar`|`_fputchar`|`_fputchar`|`_fputwchar`|  
  
## 需求  
  
|Function|必要的標頭|  
|--------------|-----------|  
|`_fputchar`|\<stdio.h\>|  
|`_fputwchar`|\<stdio.h\> 或 \<wchar.h\>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。  與主控台關聯的標準資料流控制代碼 \(`stdin`、`stdout` 和 `stderr`\) 必須重新導向，然後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。  如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_fputchar.c  
// This program uses _fputchar  
// to send a character array to stdout.  
  
#include <stdio.h>  
  
int main( void )  
{  
    char strptr[] = "This is a test of _fputchar!!\n";  
    char *p = NULL;  
  
    // Print line to stream using _fputchar.   
    p = strptr;  
    while( (*p != '\0') && _fputchar( *(p++) ) != EOF )  
      ;  
}  
```  
  
  **這是 \_fputchar 的測試\!\!**   
## .NET Framework 對等用法  
  
-   [System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)  
  
-   [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fgetc、fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [putc、putwc](../../c-runtime-library/reference/putc-putwc.md)