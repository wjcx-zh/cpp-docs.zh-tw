---
title: "_getche_nolock、_getwche_nolock | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_getche_nolock"
  - "_getwche_nolock"
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
  - "_getche_nolock"
  - "_gettche_nolock"
  - "_getwche_nolock"
  - "getche_nolock"
  - "getwche_nolock"
  - "gettche_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_getche_nolock 函式"
  - "_gettche_nolock 函式"
  - "_getwche_nolock 函式"
  - "字元, 從主控台取得"
  - "主控台, 讀取自"
  - "getche_nolock 函式"
  - "gettche_nolock 函式"
  - "getwche_nolock 函式"
ms.assetid: 9e853ad4-4d8a-4442-9ae5-da4b434f0b8c
caps.latest.revision: 18
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _getche_nolock、_getwche_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以用 echo 但不用鎖定執行緒的方式，從主控台取得字元。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _getche_nolock( void );  
wint_t _getwche_nolock( void );  
```  
  
## 傳回值  
 傳回讀取的字元。  不會回傳錯誤。  
  
## 備註  
 `_getche_nolock` 和 `_getwche_nolock` 與 `_getche` 和 `_getwche` 除了他們不會預防被其他執行續干擾之外都是一樣的。  因為它們不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。  這些函式只能用在安全執行緒內容 \(例如單一執行緒應用程式\) 或呼叫範圍已經處理執行緒隔離的地方。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_gettche_nolock`|`_getche_nolock`|`_getch_nolock`|`_getwche_nolock`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_getche_nolock`|\<conio.h\>|  
|`_getwche_nolock`|\<conio.h\> 或 \<wchar.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_getche_nolock.c  
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
      ch = _getche_nolock();  
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
 [\_cgets、\_cgetws](../../c-runtime-library/cgets-cgetws.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [\_ungetch、\_ungetwch、\_ungetch\_nolock、\_ungetwch\_nolock](../../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)