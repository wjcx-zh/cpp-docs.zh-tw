---
title: "round、roundf、roundl | Microsoft Docs"
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
  - "round"
  - "roundl"
  - "roundf"
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
  - "roundf"
  - "roundl"
  - "round"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "round 函式"
  - "roundf 函式"
  - "roundl 函式"
ms.assetid: 6be90877-193c-4b80-a32b-c3eca33f9c6f
caps.latest.revision: 6
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# round、roundf、roundl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將浮點數值捨入至最接近的整數。  
  
## 語法  
  
```  
double round(   
   double x   
);  
float round(  
   float x  
);  // C++ only  
long double round(  
   long double x  
);  // C++ only  
float roundf(  
   float x  
);  
long double roundl(  
   long double x  
);  
```  
  
#### 參數  
 `x`  
 捨入的浮點數值。  
  
## 傳回值  
 `round` 函式會傳回浮點值，代表 `x` 的最近整數。  不論浮點捨入模式的設定為何，正中間的值會以遠離零的方式捨入。  不會回傳錯誤。  
  
|輸入|SEH 例外狀況|Matherr 例外狀況|  
|--------|--------------|------------------|  
|± `QNAN`,`IND`|無|`_DOMAIN`|  
  
## 備註  
 因為 C\+\+ 允許多載，您可以呼叫會接受並傳回 `float` 和 `long double` 值的 `round` 多載。  在 C 程式，`round` 一律接受並傳回 `double`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`round`, `roundf`, `roundl`|\<math.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_round.c  
// Build with: cl /W3 /Tc crt_round.c  
// This example displays the rounded results of  
// the floating-point values 2.499999, -2.499999,   
// 2.8, -2.8, 2.5 and -2.5.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.499999;  
   float y = 2.8f;  
   long double z = 2.5;  
  
   printf("round(%f) is %.0f\n", x, round(x));  
   printf("round(%f) is %.0f\n", -x, round(-x));  
   printf("roundf(%f) is %.0f\n", y, roundf(y));  
   printf("roundf(%f) is %.0f\n", -y, roundf(-y));  
   printf("roundl(%Lf) is %.0Lf\n", z, roundl(z));  
   printf("roundl(%Lf) is %.0Lf\n", -z, roundl(-z));  
}  
```  
  
  **round\(2.499999\) 是 2**  
**round\(\-2.499999\) 是 \-2**  
**roundf\(2.800000\) 是 3**  
**roundf\(\-2.800000\) 是 \-3**  
**roundl\(2.500000\) 是 3**  
**roundl\(\-2.500000\) 是 \-3**   
## .NET Framework 對等用法  
 [System::Math::Round](https://msdn.microsoft.com/en-us/library/system.math.round.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [ceil、ceilf、ceill](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [floor、floorf、floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [fmod、fmodf](../../c-runtime-library/reference/fmod-fmodf.md)   
 [lrint、lrintf、lrintl、llrint、llrintf、llrintl](http://msdn.microsoft.com/zh-tw/312fd869-a9c0-4107-bb23-ab8299d04385)   
 [lround、lroundf、lroundl、llround、llroundf、llroundl](../../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)   
 [nearbyint、nearbyintf、nearbyintl](http://msdn.microsoft.com/zh-tw/15111e73-331d-41d1-81b7-3e10df894848)   
 [rint、rintf、rintl](../../c-runtime-library/reference/rint-rintf-rintl.md)