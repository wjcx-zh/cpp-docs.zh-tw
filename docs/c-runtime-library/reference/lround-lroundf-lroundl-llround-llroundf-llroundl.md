---
title: "lround、lroundf、lroundl、llround、llroundf、llroundl | Microsoft Docs"
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
  - "llround"
  - "llroundf"
  - "llroundl"
  - "lroundf"
  - "lround"
  - "lroundl"
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
  - "lround"
  - "lroundl"
  - "llroundl"
  - "llround"
  - "lroundf"
  - "llroundf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "llround 函式"
  - "llroundf 函式"
  - "llroundl 函式"
  - "lround 函式"
  - "lroundf 函式"
  - "lroundl 函式"
ms.assetid: cfb88a35-54c6-469f-85af-f7d695dcfdd8
caps.latest.revision: 6
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# lround、lroundf、lroundl、llround、llroundf、llroundl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將浮點數值捨入至最接近的整數。  
  
## 語法  
  
```  
long lround(   
   double x   
);  
long lround(  
   float x  
);  // C++ only  
long lround(  
   long double x  
);  // C++ only  
long lroundf(  
   float x  
);  
long lroundl(  
   long double x  
);  
long long llround(   
   double x   
);  
long long llround(  
   float x  
);  // C++ only  
long long llround(  
   long double x  
);  // C++ only  
long long llroundf(  
   float x  
);  
long long llroundl(  
   long double x  
);  
```  
  
#### 參數  
 `x`  
 捨入的浮點數值。  
  
## 傳回值  
 `lround` 和 `llround` 函式會傳回最接近的 `long` 或 `long long` 整數到 `x`。  不論浮點捨入模式的設定為何，正中間的值會以遠離零的方式捨入。  不會回傳錯誤。  
  
|輸入|SEH 例外狀況|Matherr 例外狀況|  
|--------|--------------|------------------|  
|± `QNAN`, `IND`|無|`_DOMAIN`|  
  
## 備註  
 因為 C\+\+ 允許多載，您可以呼叫會接受並傳回 `float` 和 `long double` 值的 `lround` 或 `llround` 多載。  在 C 程式，`lround` 和 `llround` 一律接受並傳回 `double`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`lround`, `lroundf`, `lroundl`, `llround`, `llroundf`, `llroundl`|\<math.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_lround.c  
// Build with: cl /W3 /Tc crt_lround.c  
// This example displays the rounded results of  
// the floating-point values 2.499999, -2.499999,   
// 2.8, -2.8, 3.5 and -3.5.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.499999;  
   float y = 2.8f;  
   long double z = 3.5;  
  
   printf("lround(%f) is %d\n", x, lround(x));  
   printf("lround(%f) is %d\n", -x, lround(-x));  
   printf("lroundf(%f) is %d\n", y, lroundf(y));  
   printf("lroundf(%f) is %d\n", -y, lroundf(-y));  
   printf("lroundl(%Lf) is %d\n", z, lroundl(z));  
   printf("lroundl(%Lf) is %d\n", -z, lroundl(-z));  
}  
```  
  
  **lround\(2.499999\) 是 2**  
**lround\(\-2.499999\) 是 \-2**  
**lroundf\(2.800000\) 是 3**  
**lroundf\(\-2.800000\) 是 \-3**  
**lroundl\(2.500000\) 是 4**  
**lroundl\(\-2.500000\) 是 \-4**   
## .NET Framework 對等用法  
 [System::Math::Round](https://msdn.microsoft.com/en-us/library/system.math.round.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [ceil、ceilf、ceill](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [floor、floorf、floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [fmod、fmodf](../../c-runtime-library/reference/fmod-fmodf.md)   
 [lrint、lrintf、lrintl、llrint、llrintf、llrintl](http://msdn.microsoft.com/zh-tw/312fd869-a9c0-4107-bb23-ab8299d04385)   
 [round、roundf、roundl](../../c-runtime-library/reference/round-roundf-roundl.md)   
 [nearbyint、nearbyintf、nearbyintl](http://msdn.microsoft.com/zh-tw/15111e73-331d-41d1-81b7-3e10df894848)   
 [rint、rintf、rintl](../../c-runtime-library/reference/rint-rintf-rintl.md)