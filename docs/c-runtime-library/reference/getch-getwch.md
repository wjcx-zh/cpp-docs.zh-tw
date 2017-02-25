---
title: "_getch、_getwch | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_getch"
  - "_getwch"
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
  - "getwch"
  - "_getch"
  - "_getwch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_getch 函式"
  - "_getwch 函式"
  - "字元, 從主控台取得"
  - "主控台, 讀取自"
  - "getch 函式"
  - "getwch 函式"
ms.assetid: cc116be7-cff2-4274-970f-5e7b18ccc05c
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# _getch、_getwch
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從主控台取得字元，不需回應。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _getch( void );  
wint_t _getwch( void );  
```  
  
## 傳回值  
 傳回讀取的字元。  不會回傳錯誤。  
  
## 備註  
 `_getch` 和`_getwch` 函式讀取從主控台的單一字元，而不用回應字元。  這些函式都不可以用來讀取 CTRL\+C。  當讀取功能鍵或方向鍵時，每個函式必須呼叫兩次;第一個呼叫會回傳0 或 0xE0，第二個呼叫會傳回實際按鍵碼。  
  
 這些函式鎖定呼叫的執行緒並具備執行緒安全。  如需非鎖定版本，請參閱 [\_getch\_nolock、\_getwch\_nolock](../../c-runtime-library/reference/getch-nolock-getwch-nolock.md)。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_gettch`|`_getch`|`_getch`|`_getwch`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_getch`|\<conio.h\>|  
|`_getwch`|\<conio.h\> 或 \<wchar.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_getch.c  
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
      ch = _getch();  
      ch = toupper( ch );  
   } while( ch != 'Y' );  
  
   _putch( ch );  
   _putch( '\r' );    // Carriage return  
   _putch( '\n' );    // Line feed    
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