---
title: "atan、atanf、atanl、atan2、atan2f、atan2l | Microsoft Docs"
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
  - "atan2f"
  - "atan2l"
  - "atan2"
  - "atanf"
  - "atan"
  - "atanl"
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
  - "atan"
  - "atan2l"
  - "atan2"
  - "atanl"
  - "atanf"
  - "atan2f"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "arctangent 函式"
  - "atan 函式"
  - "atan2 函式"
  - "atan2f 函式"
  - "atan2l 函式"
  - "atanf 函式"
  - "atanl 函式"
  - "三角函式"
ms.assetid: 7a87a18e-c94d-4727-9cb1-1bb5c2725ae4
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# atan、atanf、atanl、atan2、atan2f、atan2l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算 `x` 的反正切值 \(`atan`、 `atanf`和 `atanl`\) 或 `y`\/`x` 的反正切值 \(`atan2`、 `atan2f`和 `atan2l`\)。  
  
## 語法  
  
```  
double atan(   
   double x   
);  
float atan(  
   float x   
);  // C++ only  
long double atan(  
   long double x  
);  // C++ only  
double atan2(   
   double y,   
   double x   
);  
float atan2(  
   float y,  
   float x  
);  // C++ only  
long double atan2(  
   long double y,  
   long double x  
);  // C++ only  
float atanf(   
   float x   
);  
long double atanl(  
   long double x  
);  
float atan2f(  
   float y,  
   float x  
);  
long double atan2l(  
   long double y,  
   long double x  
);  
```  
  
#### 參數  
 `x`, `y`  
 任何數字。  
  
## 傳回值  
 `atan` 傳回 `x` 的反正切值 \(在 – π\/2 到 π\/2 的範圍中\)。  `atan2` 傳回 `y/x` 的反正切值 \(在 – π 到 π 的範圍中\)。  如果 `x` 為 0， `atan` 會傳回 0。  如果 `atan2` 的兩個參數都是 0，則函式會傳回 0。  所有結果都是以弧度為單位。  
  
 `atan2` 使用兩個參數的正負號判斷傳回值的象限。  
  
|輸入|SEH 例外狀況|Matherr 例外狀況|  
|--------|--------------|------------------|  
|± `QNAN`,`IND`|無|`_DOMAIN`|  
  
## 備註  
 `atan` 函式會計算 `x` 的反正切值 \(反正切函數函式\)。  `atan2` 計算 `y`\/`x` 的反正切值 \(`x` 等於 0 時，如果 `y` 為正數， `atan2` 會傳回 π\/2；如果 `y` 為負數，會傳回 \- π\/2；如果 `y` 是 0，會傳回 0\)。  
  
 `atan` 會使用 Streaming SIMD Extensions 2\(SSE2\) 的實作。  如需有關使用 SSE2 實作的詳細資訊和限制，請參閱 [\_set\_SSE2\_enable](../../c-runtime-library/reference/set-sse2-enable.md)。  
  
 因為 C\+\+ 允許多載，您可以呼叫 `atan` 和 `atan2` 的多載。  在 C 程式，`atan` 和 `atan2` 一律接受並傳回 double 值。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`atan`, `atan2`, `atanf`, `atan2f`, `atanl`, `atan2l`|\<math.h\>|  
  
## 範例  
  
```  
// crt_atan.c  
// arguments: 5 0.5  
#include <math.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( int ac, char* av[] )   
{  
   double x, y, theta;  
   if( ac != 3 ){  
      fprintf( stderr, "Usage: %s <x> <y>\n", av[0] );  
      return 1;  
   }  
   x = atof( av[1] );  
   theta = atan( x );  
   printf( "Arctangent of %f: %f\n", x, theta );  
   y = atof( av[2] );  
   theta = atan2( y, x );  
   printf( "Arctangent of %f / %f: %f\n", y, x, theta );   
   return 0;  
}  
```  
  
  **5.000000 的反正切值：1.373401**  
**0.500000 \/ 5.000000 的反正切值：0.099669**   
## .NET Framework 對等用法  
  
-   [System::Math::Atan](https://msdn.microsoft.com/en-us/library/system.math.atan.aspx)  
  
-   [System::Math::Atan2](https://msdn.microsoft.com/en-us/library/system.math.atan2.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [acos、acosf、acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [asin、asinf、asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [cos、cosf、cosl、cosh、coshf、coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [\_matherr](../../c-runtime-library/reference/matherr.md)   
 [sin、sinf、sinl、sinh、sinhf、sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan、tanf、tanl、tanh、tanhf、tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [\_CIatan](../../c-runtime-library/ciatan.md)   
 [\_CIatan2](../../c-runtime-library/ciatan2.md)