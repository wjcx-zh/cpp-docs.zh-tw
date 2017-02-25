---
title: "ungetc、ungetwc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "ungetwc"
  - "ungetc"
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
  - "_ungettc"
  - "ungetwc"
  - "ungetc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ungettc 函式"
  - "字元, 推送回到資料流"
  - "ungetc 函式"
  - "ungettc 函式"
  - "ungetwc 函式"
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# ungetc、ungetwc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

推一個字元到資料流上。  
  
## 語法  
  
```  
int ungetc(  
   int c,  
   FILE *stream   
);  
wint_t ungetwc(  
   wint_t c,  
   FILE *stream   
);  
```  
  
#### 參數  
 `c`  
 待推回的字元。  
  
 `stream`  
 指向 `FILE` 結構的指標。  
  
## 傳回值  
 如果成功的話，這些函式都會傳回字元引數的 `c`*。*如果 `c` 無法推回，或是未讀取字元，輸入資料流不會變更和 `ungetc` 會傳回 `EOF`; `ungetwc` 會傳回 `WEOF`。  如果 `stream` 是 `NULL`，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行， `EOF` 或 `WEOF` 會回傳並將 `errno` 設為 `EINVAL` 。  
  
 如需有關這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `ungetc` 函式推後字元 `c` 在 `stream` 上並清除檔案結尾指示器。  資料流必須開啟為唯讀。  在 `stream` 上執行後續讀取作業開頭為 `c`*。*使用 `ungetc` 被忽略而嘗試推入`EOF` 至資料流上 。  
  
 如果 `fflush`、 `fseek`、 `fsetpos`或 `rewind` 呼叫，可能會在字元從目前資料流讀取之前清除資料流位置的字元則為 `ungetc` 。  其檔案位置指示器會有值，在字元會推回之前。  與資料流相對應的外儲存不變。  在物件的文字資料流的成功呼叫 `ungetc` ，檔案位置指示器是未指定的，直到所有被推回的字元讀取或捨棄。  在對二進位資料流的每次成功呼叫 `ungetc` ，檔案位置指示器遞減;如果其值為 0，則在呼叫，值會在呼叫後未定義。  
  
 `ungetc` ，如果呼叫兩次，而兩個呼叫之間讀取或檔案當地語系化作業，結果會無法預期。  在對 `fscanf`的呼叫，對 `ungetc` 的呼叫可能會失敗後，除非另一次讀取作業 \(例如 `getc`\) 執行。  這是因為`fscanf` 會本身呼叫 `ungetc`。  
  
 `ungetwc` 是 `ungetc`的寬字元版本。  不過，在對文字或二進位資料流的每次成功呼叫 `ungetwc` ，檔案位置指示器的值未指定，直到所有被推回的字元讀取或捨棄。  
  
 這些函式是安全執行緒並在執行期間鎖定敏感性資料。  如需非鎖定版本，請參閱 [\_ungetc\_nolock、\_ungetwc\_nolock](../../c-runtime-library/reference/ungetc-nolock-ungetwc-nolock.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_ungettc`|`ungetc`|`ungetc`|`ungetwc`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`ungetc`|\<stdio.h\>|  
|`ungetwc`|\<stdio.h\> 或 \<wchar.h\>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。  與主控台關聯的標準資料流控制代碼 \(`stdin`、`stdout` 和 `stderr`\) 必須重新導向，然後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。  如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_ungetc.c  
// This program first converts a character  
// representation of an unsigned integer to an integer. If  
// the program encounters a character that is not a digit,  
// the program uses ungetc to replace it in the  stream.  
//  
  
#include <stdio.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch;  
   int result = 0;  
  
   // Read in and convert number:  
   while( ((ch = getchar()) != EOF) && isdigit( ch ) )  
      result = result * 10 + ch - '0';    // Use digit.  
   if( ch != EOF )  
      ungetc( ch, stdin );                // Put nondigit back.  
   printf( "Number = %d\nNext character in stream = '%c'",   
            result, getchar() );  
}  
```  
  
  **`521a`數字 \= 521**  
**在資料流的下一個字元「\=」。**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [putc、putwc](../../c-runtime-library/reference/putc-putwc.md)