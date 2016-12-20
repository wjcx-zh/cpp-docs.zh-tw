---
title: "acos、acosf、acosl | Microsoft Docs"
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
  - "acosf"
  - "acos"
  - "acosl"
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
  - "acos"
  - "acosl"
  - "acosf"
  - "math/acosf"
  - "math/acosl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "acos 函式"
  - "acosf 函式"
  - "acosl 函式"
  - "arccosine 函式"
  - "三角函式"
ms.assetid: 00b89c48-8faf-4824-aa95-fa4349a4975d
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# acos、acosf、acosl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算反餘弦函式。  
  
## 語法  
  
```  
double acos(   
   double x   
);  
float acos(  
   float x   
);   // C++ only  
long double acos(  
   long double x  
);   // C++ only  
float acosf(  
   float x   
);  
long double acosl(  
   long double x  
);  
```  
  
#### 參數  
 `x`  
 – 1 和 1之間的值，其可以計算反餘弦值 \(反餘弦\)。  
  
## 傳回值  
 `acos` 函式傳回 0 到 π 弧度之間的 `x` 的反餘弦函式值。  
  
 根據預設，如果 `x` 小於 \-1 或大於 1 ， `acos` 函式的回傳結果是未定義的。  
  
|輸入|SEH 例外狀況|Matherr 例外狀況|  
|--------|--------------|------------------|  
|± ∞|`INVALID`|`_DOMAIN`|  
|± QNAN,IND|無|`_DOMAIN`|  
|&#124;x&#124;\>1|`INVALID`|`_DOMAIN`|  
  
## 備註  
 因為 C\+\+ 允許多載，您可以呼叫會接受 `float`值和 `long double` 值並傳回之的 `acos` 多載。  在 C 程式，`acos` 一律接受並傳回 `double`。  
  
## 需求  
  
|常式|必要的標頭|選擇性的標頭檔|  
|--------|-----------|-------------|  
|`acos`, `acosf`, `acosl`|\<math.h\>|\<errno.h\>|  
  
## 範例  
 這個程式會提示您輸入介於 \-1 到 1 的值。  在此範圍以外的輸入值會產生 `_DOMAIN` 錯誤訊息。  如果輸入了有效的值，程式會印出它的反正弦和反餘弦函式值。  
  
```  
// crt_asincos.c  
// arguments: 0  
  
#include <math.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main( int ac, char* av[] )  
{  
    double  x,  
            y;  
    errno_t err;   
  
    // argument checking  
    if (ac != 2)  
    {  
        fprintf_s( stderr, "Usage: %s <number between -1 and 1>\n",  
                   av[0]);  
        return 1;  
    }  
  
    // Convert argument into a double value  
    if ((err = sscanf_s( av[1], "%lf", &x )) != 1)  
    {  
        fprintf_s( stderr, "Error converting argument into ",  
                   "double value.\n");  
        return 1;  
    }  
  
    // Arcsine of X  
    y = asin( x );  
    printf_s( "Arcsine of %f = %f\n", x, y );  
  
    // Arccosine of X  
    y = acos( x );  
    printf_s( "Arccosine of %f = %f\n", x, y );  
}  
```  
  
  **反正弦值 0.000000 \= 0.000000**  
**反餘弦值 0.000000 \= 1.570796**   
## .NET Framework 對等用法  
 [System::Math::Acos](https://msdn.microsoft.com/en-us/library/system.math.acos.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [asin、asinf、asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [atan、atanf、atanl、atan2、atan2f、atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [cos、cosf、cosl、cosh、coshf、coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [\_matherr](../../c-runtime-library/reference/matherr.md)   
 [sin、sinf、sinl、sinh、sinhf、sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan、tanf、tanl、tanh、tanhf、tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)