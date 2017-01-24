---
title: "getchar、getwchar | Microsoft Docs"
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
  - "getchar"
  - "getwchar"
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
  - "getwchar"
  - "GetChar"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_gettchar 函式"
  - "字元, 讀取"
  - "gettchar 函式"
  - "getwchar 函式"
  - "標準輸入, 讀取自"
ms.assetid: 19fda588-3e33-415c-bb60-dd73c028086a
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# getchar、getwchar
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從標準輸入讀取字元。  
  
## 語法  
  
```  
int getchar();  
wint_t getwchar();  
```  
  
## 傳回值  
 傳回讀取的字元。  表示讀取錯誤或文件關閉條件， `getchar` `returns EOF` 、 `getwchar` 會傳回 `WEOF`。  對於 `getchar`，請使用 `ferror` 或 `feof` 來檢查錯誤或檔案結尾。  
  
## 備註  
 每個常式讀取 `stdin` 的單一字元並將相關檔案指標指向下一個字元。  `getchar` 和 [\_fgetchar](../../c-runtime-library/reference/fgetc-fgetwc.md)相同，不過會實作為函式和當做巨集。  
  
 這些函式鎖定呼叫的執行緒並具備執行緒安全。  如需非鎖定版本，請參閱 [\_getchar\_nolock、\_getwchar\_nolock](../../c-runtime-library/reference/getchar-nolock-getwchar-nolock.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_gettchar`|`getchar`|`getchar`|`getwchar`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`getchar`|\<stdio.h\>|  
|`getwchar`|\<stdio.h\> 或 \<wchar.h\>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。  與主控台關聯的標準資料流控制代碼 \(`stdin`、`stdout` 和 `stderr`\) 必須重新導向，然後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。  如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_getchar.c  
// Use getchar to read a line from stdin.  
  
#include <stdio.h>  
  
int main()  
{  
    char buffer[81];  
    int i, ch;  
  
    for (i = 0; (i < 80) && ((ch = getchar()) != EOF)  
                         && (ch != '\n'); i++)  
    {  
        buffer[i] = (char) ch;  
    }  
  
    // Terminate string with a null character   
    buffer[i] = '\0';  
    printf( "Input was: %s\n", buffer);  
}  
```  
  
  **`This text` Input was: This text**   
## .NET Framework 對等用法  
  
-   [System::IO::StreamReader::Read](https://msdn.microsoft.com/en-us/library/system.io.streamreader.read.aspx).  
  
-   [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [fgetc、fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [\_getch、\_getwch](../../c-runtime-library/reference/getch-getwch.md)   
 [putc、putwc](../../c-runtime-library/reference/putc-putwc.md)   
 [ungetc、ungetwc](../../c-runtime-library/reference/ungetc-ungetwc.md)