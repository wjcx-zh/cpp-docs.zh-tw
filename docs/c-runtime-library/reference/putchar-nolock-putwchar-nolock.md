---
title: "_putchar_nolock、_putwchar_nolock | Microsoft Docs"
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
  - "_putchar_nolock"
  - "_putwchar_nolock"
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
apitype: "DLLExport"
f1_keywords: 
  - "putwchar_nolock"
  - "_puttchar_nolock"
  - "_putchar_nolock"
  - "_putwchar_nolock"
  - "putchar_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_putchar_nolock 函式"
  - "_puttchar_nolock 函式"
  - "_putwchar_nolock 函式"
  - "字元, 撰寫"
  - "putchar_nolock 函式"
  - "puttchar_nolock 函式"
  - "putwchar_nolock 函式"
  - "標準輸出, 寫入至"
ms.assetid: 9ac68092-bfc3-4352-b486-c3e780220575
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _putchar_nolock、_putwchar_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

寫入一個字元至**stdout**，而不用鎖定執行緒。  
  
## 語法  
  
```  
  
      int _putchar_nolock(  
   int c   
);  
wint_t _putwchar_nolock(  
   wchar_t c   
);  
  
```  
  
#### 參數  
 `c`  
 待寫入字元。  
  
## 傳回值  
 請參閱 **putchar, putwchar**。  
  
## 備註  
 **putchar\_nolock**  `和 _putwchar_nolock`的版本除了 **\_nolock** 之外都相同，但不會防止被其他執行緒干擾。  因為它們不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。  這些函式只能用在安全執行緒內容 \(例如單一執行緒應用程式\) 或呼叫範圍已經處理執行緒隔離的地方。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_puttchar_nolock`|`_putchar_nolock`|`_putchar_nolock`|`_putwchar_nolock`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_putchar_nolock`|\<stdio.h\>|  
|`_putwchar_nolock`|\<stdio.h\> 或 \<wchar.h\>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。  與主控台關聯的標準資料流控制代碼 \(`stdin`、`stdout` 和 `stderr`\) 必須重新導向，然後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。  如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_putchar_nolock.c  
/* This program uses putchar to write buffer  
 * to stdout. If an error occurs, the program  
 * stops before writing the entire buffer.  
 */  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char *p, buffer[] = "This is the line of output\n";  
   int  ch;  
  
   ch = 0;  
  
   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )  
      ch = _putchar_nolock( *p );  
}  
```  
  
## Output  
  
```  
This is the line of output  
```  
  
## .NET Framework 對等用法  
  
-   [System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)  
  
-   [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fputc、fputwc](../../c-runtime-library/reference/fputc-fputwc.md)   
 [fgetc、fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)