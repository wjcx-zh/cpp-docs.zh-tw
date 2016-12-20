---
title: "_kbhit | Microsoft Docs"
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
  - "_kbhit"
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
  - "_kbhit"
  - "kbhit"
  - "conio/_kbhit"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_kbhit 函式"
  - "主控台"
  - "主控台, 檢查"
  - "kbhit 函式"
  - "鍵盤輸入"
  - "鍵盤, 檢查輸入"
  - "鍵盤, 鍵盤輸入"
  - "使用者輸入, 檢查鍵盤"
ms.assetid: e82a1cc9-bbec-4150-b678-a7e433220fe4
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _kbhit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

檢查主控台輸入。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
  
int _kbhit( void );  
```  
  
## 傳回值  
 按下按鍵時，`_kbhit` 會傳回非零的值。  否則，會傳回 0。  
  
## 備註  
 `_kbhit` 功能檢查主控台最近的按鍵輸入。  如果函式傳回非零的值，代表有一個按鍵輸入於緩衝區等候。  程式之後可以呼叫 `_getch` 或 `_getche` 取得按鍵輸入。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_kbhit`|\<conio.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_kbhit.c  
// compile with: /c  
/* This program loops until the user  
 * presses a key. If _kbhit returns nonzero, a  
 * keystroke is waiting in the buffer. The program  
 * can call _getch or _getche to get the keystroke.  
 */  
  
#include <conio.h>  
#include <stdio.h>  
  
int main( void )  
{  
   /* Display message until key is pressed. */  
   while( !_kbhit() )  
      _cputs( "Hit me!! " );  
  
   /* Use _getch to throw key away. */  
   printf( "\nKey struck was '%c'\n", _getch() );  
}  
```  
  
## 範例輸出  
  
```  
Hit me!! Hit me!! Hit me!! Hit me!! Hit me!! Hit me!! Hit me!!  
Key struck was 'q'   
```  
  
## 請參閱  
 [主控台和連接埠 I\/O](../../c-runtime-library/console-and-port-i-o.md)