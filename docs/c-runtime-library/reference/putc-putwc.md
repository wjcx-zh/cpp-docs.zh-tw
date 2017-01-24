---
title: "putc、putwc | Microsoft Docs"
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
  - "putwc"
  - "putc"
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
  - "_puttc"
  - "putwc"
  - "putc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_puttc 函式"
  - "字元, 撰寫"
  - "putc 函式"
  - "puttc 函式"
  - "putwc 函式"
  - "資料流, 將字元寫入"
ms.assetid: a37b2e82-9d88-4565-8190-ff8d04c0ddb9
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# putc、putwc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將一個字元寫入資料流。  
  
## 語法  
  
```  
  
      int putc(  
   int c,  
   FILE *stream   
);  
wint_t putwc(  
   wchar_t c,  
   FILE *stream   
);  
```  
  
#### 參數  
 `c`  
 待寫入字元。  
  
 `stream`  
 指向 **FILE** 結構的指標。  
  
## 傳回值  
 傳回寫入的字元。  若要表示錯誤或文件關閉條件， `putc` 和 `putchar` 會傳回 `EOF`；`putwc` 和 `putwchar` 傳回 **WEOF**。  對於所有四個常式，請使用 [ferror](../../c-runtime-library/reference/ferror.md) 或 [feof](../../c-runtime-library/reference/feof.md) 來檢查錯誤或檔案結尾。  如果傳遞一個null指標給 `stream`，則如[參數驗證](../../c-runtime-library/parameter-validation.md) 所述，無效參數處理常式會被叫用。  如果允許繼續執行，這些函式會傳回 `EOF` 或 **WEOF** ，並將 `errno`設為`EINVAL`。  
  
 如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
## 備註  
 `putc` 常式在目前位置寫入單一字元`c` 至`stream` 輸出。  任何整數都可以被傳遞至 `putc`，但只有低於 8 位元組的數字會被寫入。  `putchar` 常式和 **putc\(** `c`**、stdout \)**都相同。  對於每個常式，如果讀取錯誤發生，則資料流的錯誤指示器會被設定。  `putc` 和 `putchar` 都類似於 `fputc` 和 `_fputchar`，但是都會被實作為函式和巨集 \(請參閱 [選取函式和巨集之間](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)\)。  `putwc` 和 `putwchar`  分別為 `putc` 和  `putchar` 的寬字元版本。  如果資料流是以 ANSI 模式開啟，則 `putwc` 和 `putc` 的行為相同。  `putc` 目前不支援輸出到 UNICODE 串流。  
  
 具有 **\_nolock** 結尾的版本除了不會防止被其他執行緒干擾之外都一樣。  如需詳細資訊，請參閱 **\_putc\_nolock, \_putwc\_nolock**。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_puttc`|`putc`|`putc`|**putwc**|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`putc`|\<stdio.h\>|  
|`putwc`|\<stdio.h\> 或 \<wchar.h\>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。  與主控台關聯的標準資料流控制代碼 \(`stdin`、`stdout` 和 `stderr`\) 必須重新導向，然後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。  如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_putc.c  
/* This program uses putc to write buffer  
 * to a stream. If an error occurs, the program  
 * stops before writing the entire buffer.  
 */  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char *p, buffer[] = "This is the line of output\n";  
   int  ch;  
  
   ch = 0;  
   /* Make standard out the stream and write to it. */  
   stream = stdout;  
   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )  
      ch = putc( *p, stream );  
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
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)