---
title: "div | Microsoft Docs"
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
  - "div"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "div"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "div 函式"
  - "整數相除"
  - "商數"
  - "商數, 計算"
  - "餘數計算"
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# div
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算商數和兩個整數值的餘數。  
  
## 語法  
  
```  
div_t div(   
   int numer,  
   int denom   
);  
ldiv_t div(  
   long numer,  
   long denom  
); /* C++ only */   
lldiv_t div(  
   long long numer,  
   long long denom  
); /* C++ only */  
```  
  
#### 參數  
 `numer`  
 分子。  
  
 `denom`  
 分母。  
  
## 傳回值  
 使用 `int` 型別呼叫 `div`，傳回一個型別 `div_t` 的結構 ，包含這個商數和餘數。  多載的傳回值與型別 `long` 之引數為 `ldiv_t`。  `div_t` 和 `ldiv_t` 皆在 STDLIB.H. 中定義。  
  
## 備註  
 `div` 函式會將 `denom` 除以 `numer`，因此計算其商數和餘數。  [div\_t](../../c-runtime-library/standard-types.md) 結構包含商數、`int` `quot` 和餘數 `int` `rem`。  商數的符號與數學商數的符號相同。  其絕對值是小於數學商數絕對值的最大整數。  如果分母為 0，則程式會終止並出現錯誤訊息。  
  
 取得型別 `long` 或 `long long` 引數的多載對 C\+\+ 程式碼才可供使用。  包含成員 `long` `quot` 和 `long` `rem` 的傳回型別 [ldiv\_t](../../c-runtime-library/standard-types.md)，及包含成員 `long long quot` 和 `long long rem` 的傳回型別 [lldiv\_t](../../c-runtime-library/standard-types.md)，其與`div_t` 的成員有相同的意義。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`div`|\<stdlib.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_div.c  
// arguments: 876 13  
  
// This example takes two integers as command-line  
// arguments and displays the results of the integer  
// division. This program accepts two arguments on the  
// command line following the program name, then calls  
// div to divide the first argument by the second.  
// Finally, it prints the structure members quot and rem.  
//  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <math.h>  
  
int main( int argc, char *argv[] )  
{  
   int x,y;  
   div_t div_result;  
  
   x = atoi( argv[1] );  
   y = atoi( argv[2] );  
  
   printf( "x is %d, y is %d\n", x, y );  
   div_result = div( x, y );  
   printf( "The quotient is %d, and the remainder is %d\n",  
           div_result.quot, div_result.rem );  
}  
```  
  
  **x is 876, y is 13**  
**The quotient is 67, and the remainder is 5**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [ldiv、lldiv](../../c-runtime-library/reference/ldiv-lldiv.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)