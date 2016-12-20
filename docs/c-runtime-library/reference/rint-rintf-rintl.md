---
title: "rint、rintf、rintl | Microsoft Docs"
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
  - "rintf"
  - "rintl"
  - "rint"
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
  - "rintf"
  - "rintl"
  - "rint"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rintf 函式"
  - "rint 函式"
  - "rintl 函式"
ms.assetid: 312ae3e6-278c-459a-9393-11b8f87d9184
caps.latest.revision: 8
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# rint、rintf、rintl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將浮點值四捨五入為最接近的整數，並使用浮點格式。  
  
## 語法  
  
```  
double rint( double x ); float rint( float x );  // C++ only long double rint( long double x );  // C++ only float rintf( float x );  long double rintl( long double x );    
```  
  
#### 參數  
 `x`  
 要四捨五入的浮點值。  
  
## 傳回值  
 `rint` 函式會傳回表示 `x` 的最接近整數的浮點值。  和 `nearbyint` 函式一樣，中間值會根據浮點四捨五入模式的目前設定進行四捨五入。  和 `nearbyint` 函式不一樣的是，若結果與引數的值不同，`rint` 函式可能會引發 `FE_INEXACT` 浮點例外狀況。  不會傳回錯誤。  
  
|輸入|SEH 例外狀況|`_matherr` 例外狀況|  
|--------|--------------|---------------------|  
|± ∞、QNAN、IND|無|無|  
|非正規數|EXCEPTION\_FLT\_UNDERFLOW|無|  
  
## 備註  
 因為 C\+\+ 允許多載，所以您可以呼叫採用並傳回 `float` 和 `long double` 值的 `rint` 的多載。  在 C 程式中，`rint` 會一律採用並傳回 `double`。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`rint`, `rintf`, `rintl`|\<math.h\>|\<cmath\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_rint.c  
// Build with: cl /W3 /Tc crt_rint.c  
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
  
   printf("rint(%f) is %.0f\n", x, rint (x));  
   printf("rint(%f) is %.0f\n", -x, rint (-x));  
   printf("rintf(%f) is %.0f\n", y, rintf(y));  
   printf("rintf(%f) is %.0f\n", -y, rintf(-y));  
   printf("rintl(%Lf) is %.0Lf\n", z, rintl(z));  
   printf("rintl(%Lf) is %.0Lf\n", -z, rintl(-z));  
}  
```  
  
  **rint\(2.499999\) 是 2**  
**rint\(\-2.499999\) 是 \-2**  
**rintf\(2.800000\) 是 3**  
**rintf\(\-2.800000\) 是 \-3**  
**rintl\(2.500000\) 是 3**  
**rintl\(\-2.500000\) 是 \-3**   
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
 [rint](../../c-runtime-library/reference/rint-rintf-rintl.md)