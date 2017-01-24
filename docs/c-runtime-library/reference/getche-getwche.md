---
title: "_getche、_getwche | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_getwche"
  - "_getche"
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
  - "getwche"
  - "_getche"
  - "_getwche"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_getche 函式"
  - "_getwche 函式"
  - "字元, 從主控台取得"
  - "主控台, 讀取自"
  - "getche 函式"
  - "getwche 函式"
ms.assetid: eac978a8-c43a-4130-938f-54f12e2a0fda
caps.latest.revision: 23
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _getche、_getwche
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從主控台取得包含 echo 的字元。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _getche( void );  
wint_t _getwche( void );  
```  
  
## 傳回值  
 傳回讀取的字元。  不會回傳錯誤。  
  
## 備註  
 `_getche` 和 `_getwche` 函式從主控台讀取包含 echo 的單一字元，代表字元顯示在主控台。  這些函式都不可以用來讀取 CTRL\+C。  當讀取功能鍵或方向鍵時，每個函式必須呼叫兩次;第一個呼叫會回傳0 或 0xE0，第二個呼叫會傳回實際按鍵碼。  
  
 這些函式鎖定呼叫的執行緒並具備執行緒安全。  如需非鎖定版本，請參閱 [\_getche\_nolock、\_getwche\_nolock](../../c-runtime-library/reference/getche-nolock-getwche-nolock.md)。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_getche`|`_getche`|`_getch`|`_getwche`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_getche`|\<conio.h\>|  
|`_getwche`|\<conio.h\> 或 \<wchar.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_getche.c  
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
      ch = _getche();  
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
 [\_cgets、\_cgetws](../../c-runtime-library/cgets-cgetws.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [\_ungetch、\_ungetwch、\_ungetch\_nolock、\_ungetwch\_nolock](../../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)