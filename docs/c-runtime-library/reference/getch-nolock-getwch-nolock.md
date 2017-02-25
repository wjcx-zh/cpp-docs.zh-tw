---
title: "_getch_nolock、_getwch_nolock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_getwch_nolock"
  - "_getch_nolock"
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
  - "_getch_nolock"
  - "getwch_nolock"
  - "getch_nolock"
  - "_getwch_nolock"
  - "_gettch_nolock"
  - "gettch_nolock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_getch_nolock 函式"
  - "_gettch_nolock 函式"
  - "_getwch_nolock 函式"
  - "字元, 從主控台取得"
  - "主控台, 讀取自"
  - "getch_nolock 函式"
  - "gettch_nolock 函式"
  - "getwch_nolock 函式"
ms.assetid: 9d248546-26ca-482c-b0c6-55812a987e83
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _getch_nolock、_getwch_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以不用 echo 也不用鎖定執行緒的方式，從主控台取得字元。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _getch_nolock( void );  
wint_t _getwch_nolock( void );  
```  
  
## 傳回值  
 傳回讀取的字元。  不會回傳錯誤。  
  
## 備註  
 `_getch_nolock` 和 `_getwch_nolock` 與 `_getch` 和 `_getchw` 除了他們不會預防被其他執行續干擾之外都是一樣的。  因為它們不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。  這些函式只能用在安全執行緒內容 \(例如單一執行緒應用程式\) 或呼叫範圍已經處理執行緒隔離的地方。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_gettch_nolock`|`_getch_nolock`|`_getch_nolock`|`_getwch_nolock`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_getch_nolock`|\<conio.h\>|  
|`_getwch_nolock`|\<conio.h\> 或 \<wchar.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_getch_nolock.c  
// compile with: /c  
// This program reads characters from  
// the keyboard until it receives a 'Y' or 'y'.  
  
#include <conio.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch;  
  
   _cputs( "Type 'Y' when finished typing keys: " );  
   do  
   {  
      ch = _getch_nolock();  
      ch = toupper( ch );  
   } while( ch != 'Y' );  
  
   _putch_nolock( ch );  
   _putch_nolock( '\r' );    // Carriage return  
   _putch_nolock( '\n' );    // Line feed  
}  
```  
  
  **`abcdey`按鍵輸入完成時輸入 'Y': Y**   
## NET Framework 對等  
 不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [主控台和連接埠 I\/O](../../c-runtime-library/console-and-port-i-o.md)   
 [\_getche、\_getwche](../../c-runtime-library/reference/getche-getwche.md)   
 [\_cgets、\_cgetws](../../c-runtime-library/cgets-cgetws.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [\_ungetch、\_ungetwch、\_ungetch\_nolock、\_ungetwch\_nolock](../../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)