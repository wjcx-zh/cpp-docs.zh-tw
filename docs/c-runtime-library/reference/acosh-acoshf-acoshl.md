---
title: "acosh、acoshf、acoshl | Microsoft Docs"
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
  - "acoshf"
  - "acosh"
  - "acoshl"
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
  - "acosh"
  - "acoshf"
  - "acoshl"
  - "math/acosh"
  - "math/acoshf"
  - "math/acoshl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "acoshf 函式"
  - "acosh 函式"
  - "acoshl 函式"
ms.assetid: 6985c4d7-9e2a-44ce-9a9b-5a43015f15f7
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# acosh、acoshf、acoshl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算反雙曲餘弦。  
  
## 語法  
  
```  
double acosh(  
   double x   
);  
float acosh(  
   float x   
);  // C++ only  
long double acosh(  
   long double x  
);  // C++ only  
float acoshf(  
   float x   
);  
long double acoshl(  
   long double x  
);  
```  
  
#### 參數  
 `x`  
 浮點值。  
  
## 傳回值  
 `acosh` 函式會傳回 `x` 的反雙曲餘弦 \(Arc 雙曲餘弦\)。 這些函式在網域 `x` ≥ 1 中有效。 若 `x` 小於 1，`errno` 會設為 `EDOM`，且結果為無訊息 NaN。 若 `x` 為無訊息 NaN、不確定或無限大，則會傳回相同的值。  
  
|輸入|SEH 例外狀況|`_matherr` 例外狀況|  
|--------|--------------|---------------------|  
|± QNAN、IND、INF|無|無|  
|x \< 1|無|無|  
  
## 備註  
 當您使用 C\+\+ 時，可以呼叫採用並傳回 `float` 或 `long double` 值的 `acosh` 的多載。 在 C 程式中，`acosh` 會一律採用並傳回 `double`。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`acosh`、`acoshf`、`acoshl`|\<math.h\>|\<cmath\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```c  
// crt_acosh.c  
// Compile by using: cl /W4 crt_acosh.c  
// This program displays the hyperbolic cosine of pi / 4  
// and the arc hyperbolic cosine of the result.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = cosh( pi / 4 );  
   y = acosh( x );  
   printf( "cosh( %f ) = %f\n", pi/4, x );  
   printf( "acosh( %f ) = %f\n", x, y );  
}  
```  
  
```Output  
cosh( 0.785398 ) = 1.324609 acosh( 1.324609 ) = 0.785398  
```  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [長雙精度](../../misc/long-double.md)   
 [cos、cosf、cosl、cosh、coshf、coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [sin、sinf、sinl、sinh、sinhf、sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [asinh、asinhf、asinhl](../../c-runtime-library/reference/asinh-asinhf-asinhl.md)   
 [tan、tanf、tanl、tanh、tanhf、tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [atanh、atanhf、atanhl](../../c-runtime-library/reference/atanh-atanhf-atanhl.md)   
 [\_CItan](../../c-runtime-library/citan.md)