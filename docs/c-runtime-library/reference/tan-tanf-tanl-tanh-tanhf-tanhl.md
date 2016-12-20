---
title: "tan、tanf、tanl、tanh、tanhf、tanhl | Microsoft Docs"
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
  - "tanhf"
  - "tanh"
  - "tan"
  - "tanhl"
  - "tanf"
  - "tanl"
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
  - "tanh"
  - "tan"
  - "_tanl"
  - "tanl"
  - "_tanhl"
  - "tanf"
  - "tanhf"
  - "tanhl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "tanl 函式"
  - "tanhl 函式"
  - "_tanl 函式"
  - "_tanhl 函式"
  - "tan 函式"
  - "計算正切函數"
  - "正切函數"
  - "tanh 函式"
  - "tanhf 函式"
  - "tanf 函式"
  - "三角函式"
  - "雙曲線函式"
ms.assetid: 36cc0ce8-9c80-4653-b354-ddb3b378b6bd
caps.latest.revision: 16
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tan、tanf、tanl、tanh、tanhf、tanhl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算正切 \(`tan`、 `tanf`或 `tanl`\)，或者 雙曲線正切 \(`tanh`、 `tanhf`或 `tanhl`\)。  
  
## 語法  
  
```  
double tan(  
   double x   
);  
float tan(  
   float x   
);  // C++ only  
long double tan(  
   long double x  
);  // C++ only  
float tanf(  
   float x   
);  
long double tanl(  
   long double x  
);  
double tanh(  
   double x   
);  
float tanh(  
   float x   
);  // C++ only  
long double tanh(  
   long double x  
);  // C++ only  
float tanhf(  
   float x   
);  
long double tanhl(  
   long double x  
);  
```  
  
#### 參數  
 `x`  
 角度 \(以弧度為單位\)。  
  
## 傳回值  
 `tan` 函式傳回 `x`的正切函數。  如果 `x` 大於或等於 263 或小於或等於 – 263 ，則會在結果上傳回顯著性位元遺失發生。  
  
 `tanh` 函式傳回 `x`的雙曲線正切函數。  不會回傳錯誤。  
  
|輸入|SEH 例外狀況|`Matherr` 例外狀況|  
|--------|--------------|--------------------|  
|± QNAN,IND|無|\_DOMAIN|  
|± ∞  \(`tan`, `tanf`\)|`INVALID`|\_DOMAIN|  
  
## 備註  
 因為 C\+\+ 允許多載，您可以呼叫會接受並傳回 `float` 或 `long double` 值的 `tan` 和 `tanh` 多載。  在 C 程式，`tan` 和 `tanh` 一律接受並傳回 `double`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`tan`, `tanf`, `tanl`, `tanh`, `tanhf`, `tanhl`|\<math.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_tan.c  
// This program displays the tangent of pi / 4  
// and the hyperbolic tangent of the result.  
//  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = tan( pi / 4 );  
   y = tanh( x );  
   printf( "tan( %f ) = %f\n", pi/4, x );  
   printf( "tanh( %f ) = %f\n", x, y );  
}  
```  
  
  **tan\( 0.785398 \) \= 1.000000**  
**tanh\( 1.000000 \) \= 0.761594**   
## .NET Framework 對等用法  
  
-   [System::Math::Tan](https://msdn.microsoft.com/en-us/library/system.math.tan.aspx)  
  
-   [System::Math::Tanh](https://msdn.microsoft.com/en-us/library/system.math.tanh.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [長雙精度](../../misc/long-double.md)   
 [acos、acosf、acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [asin、asinf、asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [atan、atanf、atanl、atan2、atan2f、atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [cos、cosf、cosl、cosh、coshf、coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [sin、sinf、sinl、sinh、sinhf、sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [\_CItan](../../c-runtime-library/citan.md)