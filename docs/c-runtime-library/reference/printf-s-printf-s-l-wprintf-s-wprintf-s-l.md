---
title: "printf_s、_printf_s_l、wprintf_s、_wprintf_s_l | Microsoft Docs"
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
  - "_printf_s_l"
  - "wprintf_s"
  - "_wprintf_s_l"
  - "printf_s"
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
  - "wprintf_s"
  - "printf_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_printf_s_l 函式"
  - "_tprintf_s 函式"
  - "_tprintf_s_l 函式"
  - "_wprintf_s_l 函式"
  - "格式化的文字 [C++]"
  - "printf 函式, 格式規格欄位"
  - "printf 函式, 使用"
  - "printf_s 函式"
  - "printf_s_l 函式"
  - "tprintf_s 函式"
  - "tprintf_s_l 函式"
  - "wprintf_s 函式"
  - "wprintf_s_l 函式"
ms.assetid: 044ebb2e-5cc1-445d-bb4c-f084b405615b
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# printf_s、_printf_s_l、wprintf_s、_wprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

列印格式化的輸出到標準輸出資料流。  這些 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 版本有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
int printf_s(  
   const char *format [,  
   argument]...   
);  
int _printf_s_l(  
   const char *format,  
   locale_t locale [,  
   argument]...   
);  
int wprintf_s(  
   const wchar_t *format [,  
   argument]...   
);  
int _wprintf_s_l(  
   const wchar_t *format,  
   locale_t locale [,  
   argument]...   
);  
```  
  
#### 參數  
 `format`  
 格式控制。  
  
 `argument`  
 選擇性引數。  
  
 `locale`  
 使用的地區設定。  
  
## 傳回值  
 傳回列印的字元數，或傳回負值表示發生錯誤。  
  
## 備註  
 `printf_s` 函式會格式化一連串的字元和數值並列印到標準輸出資料流 `stdout`。  如果 *format* 字串後有接續其他參數，則 `format` 字串必須包含指明其他參數的輸出格式的訊息。  
  
 `printf_s` 和 `printf` 之間的主要差異在於 `printf_s` 會檢查格式字串裏的無效格式字元，而 `printf` 只檢查格式字串是否為空指標。  如果的任一檢查失敗，一個無效參數的處理常式會被調用，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，函式會傳回 \-1 並將 `errno` 設定為 `EINVAL`。  
  
 如需 `errno` 和錯誤碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 `printf_s`  和 `fprintf_s` 行為上相同，除了 `printf_s` 寫入輸出到 `stdout` 而不是以 `FILE` 類別為目標。  如需詳細資訊，請參閱[fprintf\_s、\_fprintf\_s\_l、fwprintf\_s、\_fwprintf\_s\_l](../../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)。  
  
 `wprintf_s` 是 `printf_s` 的寬字元版本，`format` 是寬字元字串。  如果資料流是以 ANSI 模式開啟，則 `wprintf_s` 和 `printf_s` 的行為相同。  `printf_s` 目前不支援輸出到 UNICODE 串流。  
  
 尾碼為 `_l` 的這些函式版本是一樣的，只不過它們使用傳入的地區設定，而不是目前執行緒的地區設定。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_unicode|  
|----------------|----------------------------|----------------|-------------------|  
|`_tprintf_s`|`printf_s`|`printf_s`|`wprintf_s`|  
|`_tprintf_s_l`|`_printf_s_l`|`_printf_s_l`|`_wprintf_s_l`|  
  
 `format` 引數包含一般字元、逸出序列和 \(如果引數接在 `format` 後面的話\) 格式規格。  一般字元和逸出序列會依照它們出現的順序複製到 `stdout`。  例如，此行  
  
```  
printf_s("Line one\n\t\tLine two\n");   
```  
  
 會產生輸出  
  
```  
Line one  
        Line two  
```  
  
 [格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)永遠以百分比符號 \(`%`\) 開頭並由左至右讀取。  當 `printf_s` 遇到第一個格式規格 \(如果有的話\)，則會轉換在 `format` 後的第一個參數的值並據以輸出它。  第二個格式規格會使第二個引數被轉換和輸出，依此類推。  如果參數的個數比格式規格的數目還多，將會忽略額外的引數。  如果引數個數不足以供所有格式規格使用，結果是未定義的。  
  
> [!IMPORTANT]
>  確認 `format` 不是使用者定義的字串。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`printf_s`, `_printf_s_l`|\<stdio.h\>|  
|`wprintf_s`, `_wprintf_s_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。  與主控台關聯的標準資料流控制代碼 \(`stdin`、`stdout` 和 `stderr`\) 必須重新導向，然後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。  如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_printf_s.c  
/* This program uses the printf_s and wprintf_s functions  
 * to produce formatted output.  
 */  
  
#include <stdio.h>  
  
int main( void )  
{  
   char   ch = 'h', *string = "computer";  
   int    count = -9234;  
   double fp = 251.7366;  
   wchar_t wch = L'w', *wstring = L"Unicode";  
  
   /* Display integers. */  
   printf_s( "Integer formats:\n"  
           "   Decimal: %d  Justified: %.6d  Unsigned: %u\n",  
           count, count, count );  
  
   printf_s( "Decimal %d as:\n   Hex: %Xh  C hex: 0x%x  Octal: %o\n",  
            count, count, count, count );  
  
   /* Display in different radixes. */  
   printf_s( "Digits 10 equal:\n   Hex: %i  Octal: %i  Decimal: %i\n",  
            0x10, 010, 10 );  
  
   /* Display characters. */  
  
   printf_s("Characters in field (1):\n%10c%5hc%5C%5lc\n", ch, ch, wch, wch);  
   wprintf_s(L"Characters in field (2):\n%10C%5hc%5c%5lc\n", ch, ch, wch, wch);  
  
   /* Display strings. */  
  
   printf_s("Strings in field (1):\n%25s\n%25.4hs\n   %S%25.3ls\n",  
   string, string, wstring, wstring);  
   wprintf_s(L"Strings in field (2):\n%25S\n%25.4hs\n   %s%25.3ls\n",  
       string, string, wstring, wstring);  
  
   /* Display real numbers. */  
   printf_s( "Real numbers:\n   %f %.2f %e %E\n", fp, fp, fp, fp );  
  
   /* Display pointer. */  
   printf_s( "\nAddress as:   %p\n", &count);  
  
}  
```  
  
## 範例輸出  
  
```  
Integer formats:  
   Decimal: -9234  Justified: -009234  Unsigned: 4294958062  
Decimal -9234 as:  
   Hex: FFFFDBEEh  C hex: 0xffffdbee  Octal: 37777755756  
Digits 10 equal:  
   Hex: 16  Octal: 8  Decimal: 10  
Characters in field (1):  
         h    h    w    w  
Characters in field (2):  
         h    h    w    w  
Strings in field (1):  
                 computer  
                     comp  
   Unicode                      Uni  
Strings in field (2):  
                 computer  
                     comp  
   Unicode                      Uni  
Real numbers:  
   251.736600 251.74 2.517366e+002 2.517366E+002  
  
Address as:   0012FF78  
  
```  
  
## .NET Framework 對等用法  
  
-   [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
-   [System::Console::WriteLine](https://msdn.microsoft.com/en-us/library/system.console.writeline.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [vprintf 函式](../../c-runtime-library/vprintf-functions.md)