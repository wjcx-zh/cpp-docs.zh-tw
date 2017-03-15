---
title: "_fgetchar、_fgetwchar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fgetchar"
  - "_fgetwchar"
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
  - "fgetwchar"
  - "_fgettchar"
  - "_fgetchar"
  - "_fgetwchar"
  - "fgettchar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fgetchar 函式"
  - "_fgettchar 函式"
  - "_fgetwchar 函式"
  - "fgetchar 函式"
  - "fgettchar 函式"
  - "fgetwchar 函式"
  - "標準輸入, 讀取自"
ms.assetid: 8bce874c-701a-41a3-b1b2-feff266fb5b9
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# _fgetchar、_fgetwchar
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從 `stdin` 讀取字元。  
  
## 語法  
  
```  
int _fgetchar( void );  
wint_t _fgetwchar( void );  
```  
  
## 傳回值  
 `_fgetchar` 傳回作為 `int` 讀取的字元或傳回`EOF` 表示錯誤或檔案結尾。  **\_**`fgetwchar` 傳回對應至讀取的字元寬字元或傳回 `WEOF` 以指出錯誤或檔案結尾，如 [wint\_t](../../c-runtime-library/standard-types.md)。  對於兩個函式，請使用 `feof` 或 `ferror` 區別錯誤和文件結尾條件。  
  
## 備註  
 這些函式讀取來自 `stdin` 的單一字元。  函式會將關聯的檔案指標 \(如果有定義\)指向下一個字元。  如果資料流已在檔案結尾，資料流的檔案結尾標記會被設定。  
  
 `_fgetchar` 相當於 `fgetc( stdin )`。  它也相當於 `getchar`，不過，只有實作為函式，而不是函式和巨集。  `_fgetwchar` 是 `_fgetchar`的寬字元版本。  
  
 這些函式與 ANSI 標準不相容。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_fgettchar`|`_fgetchar`|`_fgetchar`|`_fgetwchar`|  
  
## 需求  
  
|Function|必要的標頭|  
|--------------|-----------|  
|`_fgetchar`|\<stdio.h\>|  
|`_fgetwchar`|\<stdio.h\> 或 \<wchar.h\>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。  與主控台關聯的標準資料流控制代碼 \(`stdin`、`stdout` 和 `stderr`\) 必須重新導向，然後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。  如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_fgetchar.c  
// This program uses _fgetchar to read the first  
// 80 input characters (or until the end of input)  
// and place them into a string named buffer.  
//  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char buffer[81];  
   int  i, ch;  
  
   // Read in first 80 characters and place them in "buffer":  
   ch = _fgetchar();  
   for( i=0; (i < 80 ) && ( feof( stdin ) == 0 ); i++ )  
   {  
      buffer[i] = (char)ch;  
      ch = _fgetchar();  
   }  
  
   // Add null to end string   
   buffer[i] = '\0';  
   printf( "%s\n", buffer );  
}  
```  
  
  **`Line one. Line two.`Line one.**  
**Line two.**   
## .NET Framework 對等用法  
  
-   [System::IO::StreamReader::Read](https://msdn.microsoft.com/en-us/library/system.io.streamreader.read.aspx).  
  
-   [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fputc、fputwc](../../c-runtime-library/reference/fputc-fputwc.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)