---
title: "_ungetch、_ungetwch、_ungetch_nolock、_ungetwch_nolock | Microsoft Docs"
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
  - "_ungetch_nolock"
  - "_ungetwch_nolock"
  - "_ungetwch"
  - "_ungetch"
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
  - "api-ms-win-crt-conio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_ungetch_nolock"
  - "ungetwch"
  - "ungetch_nolock"
  - "_ungetwch"
  - "ungetch"
  - "ungetwch_nolock"
  - "_ungetch"
  - "_ungettch_nolock"
  - "_ungettch"
  - "_ungetwch_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ungetch 函式"
  - "_ungetch_nolock 函式"
  - "_ungettch 函式"
  - "_ungettch_nolock 函式"
  - "_ungetwch 函式"
  - "_ungetwch_nolock 函式"
  - "字元, 推送回到主控台"
  - "ungetch_nolock 函式"
  - "ungettch 函式"
  - "ungettch_nolock 函式"
  - "ungetwch 函式"
  - "ungetwch_nolock 函式"
ms.assetid: 70ae71c6-228c-4883-a57d-de6d5f873825
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ungetch、_ungetwch、_ungetch_nolock、_ungetwch_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

推回從主控台讀取的最後一個字元。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _ungetch(  
   int c   
);  
wint_t _ungetwch(  
   wint_t c   
);  
int _ungetch_nolock(  
   int c   
);  
wint_t _ungetwch_nolock(  
   wint_t c   
);  
```  
  
#### 參數  
 `c`  
 待推回的字元。  
  
## 傳回值  
 如果成功，則兩個函式傳回字元 `c` 。  如果有錯誤， `_ungetch` 傳回 `EOF` 的值，並且 `_ungetwch`會傳回`WEOF`。  
  
## 備註  
 這些函式會將字元 `c` 推回主控台，讓 `c` 成為 `_getch` 或 `_getche` 下一個要讀取的字元 \(或`_getwch`，或`_getwche`\)。  如果在下一個讀取前呼叫超過一次，則 `_ungetch` 和 `_ungetwch` 會失敗。  `c` 引數不可以是 `EOF` \(或 `WEOF`\)。  
  
 有 `_nolock` 結尾的版本是相同的，除非它們受到其他執行緒干擾。  因為它們不會造成鎖定其他執行緒的額外負荷，所以會比較快。  這些函式只能用在安全執行緒內容 \(例如單一執行緒應用程式\) 或呼叫範圍已經處理執行緒隔離的地方。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_ungettch`|`_ungetch`|`_ungetch`|`_ungetwch`|  
|`_ungettch_nolock`|`_ungetch_nolock`|`_ungetch_nolock`|`_ungetwch_nolock`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_ungetch`, `_ungetch_nolock`|\<conio.h\>|  
|`_ungetwch`, `_ungetwch_nolock`|\<conio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_ungetch.c  
// compile with: /c  
// In this program, a white-space delimited   
// token is read from the keyboard. When the program   
// encounters a delimiter, it uses _ungetch to replace   
// the character in the keyboard buffer.  
//  
  
#include <conio.h>  
#include <ctype.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char buffer[100];  
   int count = 0;  
   int ch;  
  
   ch = _getche();  
   while( isspace( ch ) )      // Skip preceding white space.  
      ch = _getche();  
   while( count < 99 )         // Gather token.  
   {  
      if( isspace( ch ) )      // End of token.  
         break;  
      buffer[count++] = (char)ch;  
      ch = _getche();  
   }  
   _ungetch( ch );            // Put back delimiter.  
   buffer[count] = '\0';      // Null terminate the token.  
   printf( "\ntoken = %s\n", buffer );  
}  
```  
  
  **`White`語彙基元 \= White**   
## 請參閱  
 [主控台和連接埠 I\/O](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cscanf、\_cscanf\_l、\_cwscanf、\_cwscanf\_l](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)   
 [\_getch、\_getwch](../../c-runtime-library/reference/getch-getwch.md)