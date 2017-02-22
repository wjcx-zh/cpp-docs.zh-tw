---
title: "frexp | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "frexp"
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
  - "api-ms-win-crt-math-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "frexp"
  - "_frexpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_frexpl 函式"
  - "指數, 浮點數"
  - "浮點函式, 尾數和指數"
  - "frexp 函式"
  - "frexpl 函式"
  - "尾數, 浮點變數"
ms.assetid: 9b020f2e-3967-45ec-a6a8-d467a071aa55
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# frexp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得浮點數的尾數和指數。  
  
## 語法  
  
```  
double frexp(  
   double x,  
   int *expptr   
);  
float frexp(  
   float x,  
   int * expptr  
);  // C++ only  
long double frexp(  
   long double x,  
   int * expptr  
);  // C++ only  
```  
  
#### 參數  
 `x`  
 浮點值  
  
 `expptr`  
 要儲存的整數指標的指標。  
  
## 傳回值  
 `frexp`傳回尾數。  如果 `x` 為 0，則函式會傳回 0 尾數和指數的。  如果 `expptr` 為 `NULL`，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，函式將 `errno` 設置為 `EINVAL` 並回傳 0 。  
  
## 備註  
 `frexp` 函式為尾數 \(`m`\) 除以浮點值 \(`x`\) 和指數 \(`n`\)，這種 `m` 的絕對值大於或等於 0.5 且小於 1.0 且 `x` \= `m`\*2。<sup>n</sup> 整數指數 `n` 位置儲存指向 `expptr`。  
  
 C\+\+ 允許多載，因此您可以呼叫 `frexp` 不同版本的多載。  在 C\+\+ 程式， `frexp` 一律採用雙和整數並傳回雙精度浮點數。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`frexp`|\<math.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_frexp.c  
// This program calculates frexp( 16.4, &n )  
// then displays y and n.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x, y;  
   int n;  
  
   x = 16.4;  
   y = frexp( x, &n );  
   printf( "frexp( %f, &n ) = %f, n = %d\n", x, y, n );  
}  
```  
  
  **frexp \(16.400000， &n\) \= 0.512500， n \= 5**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [ldexp](../../c-runtime-library/reference/ldexp.md)   
 [modf、 modff modfl](../../c-runtime-library/reference/modf-modff-modfl.md)