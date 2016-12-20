---
title: "modf、 modff modfl | Microsoft Docs"
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
  - "modff"
  - "modf"
  - "modfl"
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
  - "modff"
  - "_modfl"
  - "modf"
  - "modfl"
  - "math/modf"
  - "math/modff"
  - "math/modfl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "modf 函式"
  - "modff 函式"
  - "modfl 函式"
ms.assetid: b1c7abf5-d476-43ca-a03c-02072a86e32d
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# modf、 modff modfl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

分割成小數的浮點值和整數部分。  
  
## 語法  
  
```  
double modf(  
   double x,  
   double * intptr   
);  
float modf(  
   float x,  
   float * intptr  
);  // C++ only  
long double modf(  
   long double x,  
   long double * intptr  
);  // C++ only  
float modff(  
   float x,  
   float * intptr   
);  
long double modfl(  
   long double x,  
   long double * intptr  
);  
```  
  
#### 參數  
 *x*  
 浮點值。  
  
 `intptr`  
 預存的整數部分的指標。  
  
## 傳回值  
 此函式傳回的帶正負號的小數部分的 *x*。 不會傳回錯誤。  
  
## 備註  
 `modf` 細分的浮點值的函式 `x` 到小數和整數部分，每一個都有相同的簽章為 `x`。 帶正負號的小數部分的 `x` 會傳回。 整數部分會儲存為浮點值 `intptr.`  
  
 `modf` 有使用 Streaming SIMD Extensions 2 \(SSE2\) 的實作。 請參閱 [\_set\_SSE2\_enable](../../c-runtime-library/reference/set-sse2-enable.md) 資訊和使用 SSE2 實作的限制。  
  
 C \+ \+ 允許多載，因此您可以呼叫的多載 `modf` 採用並傳回 `float` 或 `long double` 參數。 在 C 程式中， `modf` 一律採用兩個雙精度浮點數值並傳回雙精度浮點數值。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`modf`, `modff`, `modfl`|C: \< h.h \><br /><br /> C \+ \+:、 \< h \> 或 \< h.h \>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## 範例  
  
```  
// crt_modf.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x, y, n;  
  
   x = -14.87654321;      /* Divide x into its fractional */  
   y = modf( x, &n );     /* and integer parts            */  
  
   printf( "For %f, the fraction is %f and the integer is %.f\n",   
           x, y, n );  
}  
```  
  
## 輸出  
  
```  
For -14.876543, the fraction is -0.876543 and the integer is -14  
```  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)   
 [ldexp](../../c-runtime-library/reference/ldexp.md)