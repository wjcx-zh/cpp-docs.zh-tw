---
title: "putchar、putwchar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "putchar"
  - "putwchar"
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
  - "putchar"
  - "putwchar"
  - "_puttchar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_puttchar 函式"
  - "字元, 撰寫"
  - "putchar 函式"
  - "putwchar 函式"
  - "標準輸出, 寫入至"
ms.assetid: 93657c7f-cca1-4032-8e3a-cd6ab6193748
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# putchar、putwchar
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

寫入一個字元給 **stdout**。  
  
## 語法  
  
```  
  
      int putchar(  
   int c   
);  
wint_t putwchar(  
   wchar_t c   
);  
```  
  
#### 參數  
 `c`  
 待寫入字元。  
  
## 傳回值  
 傳回寫入的字元。  若要表示錯誤或文件關閉條件， `putc` 和 `putchar` 會傳回 `EOF`；`putwc` 和 `putwchar` 傳回 **WEOF**。  對於所有四個常式，請使用 [ferror](../../c-runtime-library/reference/ferror.md) 或 [feof](../../c-runtime-library/reference/feof.md) 來檢查錯誤或檔案結尾。  如果傳遞一個 null 指標給 `stream`，這些函式會產生一個無效的參數例外狀況，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，它們會傳回 `EOF` 或 **WEOF**，並將 `errno` 設定為`EINVAL`。  
  
 如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
## 備註  
 `putc` 常式給輸出 `stream` 的目前位置寫入單一字元 `c`。  任何整數可以傳遞至 `putc`，但只有較低 8 位元組會寫入。  `putchar` 常式和 **putc\(** `c`**、stdout \)**都相同。  對於每個常式，，如果讀取錯誤發生，資料流的錯誤指示器會被設定。  `putc` 和 `putchar` 分別是類似於 `fputc` 和 `_fputchar`，但是都會被實作為函式和巨集 \(請參閱 [選取函式和巨集之間](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)\)。  `putwc` 和 `putwchar`  分別為 `putc` 和  `putchar` 的寬字元版本。  
  
 與 **\_nolock** 結尾的版本相同，但不會防止被其他執行緒干擾。  因為它們不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。  這些函式只能用在安全執行緒內容 \(例如單一執行緒應用程式\) 或呼叫範圍已經處理執行緒隔離的地方。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_puttchar`|`putchar`|`putchar`|**putwchar**|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`putchar`|\<stdio.h\>|  
|`putwchar`|\<stdio.h\> 或 \<wchar.h\>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。  與主控台關聯的標準資料流控制代碼 \(`stdin`、`stdout` 和 `stderr`\) 必須重新導向，然後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。  如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_putchar.c  
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
  
   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )  
      ch = putchar( *p );  
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