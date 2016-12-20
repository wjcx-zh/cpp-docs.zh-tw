---
title: "atanh、atanhf、atanhl | Microsoft Docs"
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
  - "atanhl"
  - "atanhf"
  - "atanh"
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
  - "atanhl"
  - "atanhf"
  - "atanh"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "atanh 函式"
  - "atanhf 函式"
  - "atanhl 函式"
ms.assetid: 83a43b5b-2580-4461-854f-dc84236d9f32
caps.latest.revision: 8
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# atanh、atanhf、atanhl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算反雙曲正切。  
  
## 語法  
  
```  
double atanh(    double x  ); float atanh(    float x  );  // C++ only long double atanh(    long double x );  // C++ only float atanhf(    float x  ); long double atanhl(    long double x );  
```  
  
#### 參數  
 `x`  
 浮點值。  
  
## 傳回值  
 `atanh` 函式會傳回 `x` 的反雙曲正切 \(Arc 雙曲正切\)。  若 `x` 大於 1，或小於 –1，`errno` 會設為 `EDOM`，且結果為無訊息 NaN。  若 `x` 等於 1 或 \-1，則會分別傳回無限大的正數或負數，且 `errno` 會設為 `ERANGE`。  
  
|輸入|SEH 例外狀況|`Matherr` 例外狀況|  
|--------|--------------|--------------------|  
|± QNAN、IND|無|無|  
|`X` ≥ 1; `x` ≤ \-1|無|無|  
  
## 備註  
 因為 C\+\+ 允許多載，所以您可以呼叫採用並傳回 `float` 或 `long double` 值的 `atanh` 的多載。  在 C 程式中，`atanh` 會一律採用並傳回 `double`。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`atanh`, `atanhf`, `atanhl`|\<math.h\>|\<cmath\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_atanh.c  
// This program displays the hyperbolic tangent of pi / 4  
// and the arc hyperbolic tangent of the result.  
//  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = tanh( pi / 4 );  
   y = atanh( x );  
   printf( "tanh( %f ) = %f\n", pi/4, x );  
   printf( "atanh( %f ) = %f\n", x, y );  
}  
```  
  
  **tanh\( 0.785398 \) \= 0.655794**  
**atanh\( 0.655794 \) \= 0.785398**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [長雙精度](../../misc/long-double.md)   
 [acos、acosf、acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [asin、asinf、asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [atan、atanf、atanl、atan2、atan2f、atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [cos、cosf、cosl、cosh、coshf、coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [sin、sinf、sinl、sinh、sinhf、sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan、tanf、tanl、tanh、tanhf、tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [\_CItan](../../c-runtime-library/citan.md)