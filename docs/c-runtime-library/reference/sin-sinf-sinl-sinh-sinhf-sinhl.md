---
title: "sin、sinf、sinl、sinh、sinhf、sinhl | Microsoft Docs"
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
  - "sinl"
  - "sinf"
  - "sinhf"
  - "sinh"
  - "sin"
  - "sinhl"
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
  - "_sinl"
  - "sinf"
  - "sinhl"
  - "sinl"
  - "sin"
  - "sinhf"
  - "_sinhl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_sinhl 函式"
  - "_sinl 函式"
  - "計算正弦函數"
  - "雙曲線函式"
  - "sin 函式"
  - "sinf 函式"
  - "sinh 函式"
  - "sinhf 函式"
  - "sinhl 函式"
  - "sinl 函式"
  - "三角函式"
ms.assetid: 737de73e-3590-45f9-8257-dc1c0c489dfc
caps.latest.revision: 16
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# sin、sinf、sinl、sinh、sinhf、sinhl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算正弦函數和雙曲線正弦函數。  
  
## 語法  
  
```  
double sin(  
   double x   
);  
float sin(  
   float x  
);  // C++ only  
long double sin(  
   long double x  
);  // C++ only  
float sinf(  
   float x   
);  
long double sinl(  
   long double x  
);  
double sinh(  
   double x   
);  
float sinh(  
   float x   
);  // C++ only  
long double sinh(  
   long double x  
);  // C++ only  
float sinhf(  
   float x  
);  
long double sinhl(  
   long double x  
);  
```  
  
#### 參數  
 `x`  
 角度 \(以弧度為單位\)。  
  
## 傳回值  
 `sin` 函式傳回 `x` 的正弦函數。  如果 `x` 大於或等於 263 ，或者小於或等於 – 263 ，會造成喪失意義的結果。  
  
 `sinh` 函式傳回 `x` 的雙曲線正弦函數。  根據預設，若結果太大，`sinh` 會將`ERANGE` 設為 `errno` 並傳回 ± `HUGE_VAL`。  
  
|輸入|SEH 例外狀況|Matherr 例外狀況|  
|--------|--------------|------------------|  
|± QNAN,IND|None|\_DOMAIN|  
|± ∞ \(sin、sinf、sinl\)|INVALID|\_DOMAIN|  
|&#124;x&#124; ≥ 7.104760e\+002 \(sinh, sinhf, sinhl\)|OVERFLOW\+INEXACT|OVERFLOW|  
  
 如需傳回碼的詳細資訊，請參閱[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 因為 C\+\+ 允許多載，您可以呼叫會接受並傳回 `float` 或 `long double` 值的 `sin` 和 `sinh` 之多載。  在 C 程式，`sin` 和 `sinh` 一律接受並傳回 `double`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`sin`, `sinf`, `sinl`, `sinh`, `sinhf`, `sinhl`|\<math.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_sincos.c  
// This program displays the sine, hyperbolic  
// sine, cosine, and hyperbolic cosine of pi / 2.  
//  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = pi / 2;  
   y = sin( x );  
   printf( "sin( %f ) = %f\n", x, y );  
   y = sinh( x );  
   printf( "sinh( %f ) = %f\n",x, y );  
   y = cos( x );  
   printf( "cos( %f ) = %f\n", x, y );  
   y = cosh( x );  
   printf( "cosh( %f ) = %f\n",x, y );  
}  
```  
  
  **sin\( 1.570796 \) \= 1.000000**  
**sinh\( 1.570796 \) \= 2.301299**  
**cos\( 1.570796 \) \= 0.000000**  
**cosh\( 1.570796 \) \= 2.509178**   
## .NET Framework 對等用法  
  
-   [System::Math::Sin](https://msdn.microsoft.com/en-us/library/system.math.sin.aspx)  
  
-   [System::Math::Sinh](https://msdn.microsoft.com/en-us/library/system.math.sinh.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [acos、acosf、acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [asin、asinf、asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [atan、atanf、atanl、atan2、atan2f、atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [cos、cosf、cosl、cosh、coshf、coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [tan、tanf、tanl、tanh、tanhf、tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [\_CIsin](../../c-runtime-library/cisin.md)