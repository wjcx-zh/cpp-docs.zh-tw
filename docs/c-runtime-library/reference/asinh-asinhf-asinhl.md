---
title: "asinh、asinhf、asinhl | Microsoft Docs"
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
  - "asinh"
  - "asinhf"
  - "asinhl"
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
  - "asinhf"
  - "asinhl"
  - "asinh"
dev_langs: 
  - "C++"
ms.assetid: 4488babe-1a7e-44ca-8b7b-c2db0a70084f
caps.latest.revision: 7
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# asinh、asinhf、asinhl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算反雙曲正弦。  
  
## 語法  
  
```  
double asinh(    double x  ); float asinh(    float x  );  // C++ only long double asinh(    long double x );  // C++ only float asinhf(    float x  ); long double asinhl(    long double x );  
```  
  
#### 參數  
 `x`  
 浮點值。  
  
## 傳回值  
 `asinh` 函式會傳回 `x` 的反雙曲正弦 \(Arc 雙曲正弦\)。  此函式在浮點網域中有效。  若 `x` 為無訊息 NaN、不確定或無限大，則會傳回相同的值。  
  
|輸入|SEH 例外狀況|`_matherr` 例外狀況|  
|--------|--------------|---------------------|  
|± QNAN、IND、INF|無|無|  
  
## 備註  
 當您使用 C\+\+ 時，可以呼叫採用並傳回 `float` 或 `long double` 值的 `asinh` 的多載。  在 C 程式中，`asinh` 會一律採用並傳回 `double`。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`asinh`, `asinhf`, `asinhl`|\<math.h\>|\<cmath\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```c  
// crt_asinh.c  
// Compile by using: cl /W4 crt_asinh.c  
// This program displays the hyperbolic sine of pi / 4  
// and the arc hyperbolic sine of the result.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = sinh( pi / 4 );  
   y = asinh( x );  
   printf( "sinh( %f ) = %f\n", pi/4, x );  
   printf( "asinh( %f ) = %f\n", x, y );  
}  
```  
  
  **sinh\( 0.785398 \) \= 0.868671**  
**asinh\( 0.868671 \) \= 0.785398**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [長雙精度](../../misc/long-double.md)   
 [cos、cosf、cosl、cosh、coshf、coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [acosh、acoshf、acoshl](../../c-runtime-library/reference/acosh-acoshf-acoshl.md)   
 [sin、sinf、sinl、sinh、sinhf、sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan、tanf、tanl、tanh、tanhf、tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [atanh、atanhf、atanhl](../../c-runtime-library/reference/atanh-atanhf-atanhl.md)   
 [\_CItan](../../c-runtime-library/citan.md)