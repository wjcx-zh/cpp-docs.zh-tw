---
title: "ldexp | Microsoft Docs"
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
  - "ldexp"
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
  - "ldexp"
  - "_ldexpl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "計算實數"
  - "計算實數"
  - "指數, 浮點數"
  - "浮點函式, 尾數和指數"
  - "ldexp 函式"
  - "尾數, 浮點變數"
ms.assetid: aa7f5310-3879-4f63-ae74-86a39fbdedfa
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ldexp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將浮點數與 2 的整數冪相乘。  
  
## 語法  
  
```  
double ldexp(    double x,    int exp  ); float ldexp(    float x,    int exp );  // C++ only long double ldexp(    long double x,    int exp );  // C++ only  float ldexpf(    float x,    int exp );  long double ldexpl(    long double x,    int exp );   
```  
  
#### 參數  
 `x`  
 浮點值。  
  
 `exp`  
 整數指數。  
  
## 傳回值  
 若成功，`ldexp` 函數會傳回 `x` \* 2<sup>exp</sup> 的值。  溢位且根據 `x` 的符號時，`ldexp` 會傳回 \+\/– `HUGE_VAL`；`errno` 值會設為 `ERANGE`。  
  
 如需有關 `errno` 和其他可能的錯誤傳回值的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 因為 C\+\+ 允許多載，所以您可以呼叫採用 `float` 和 `long double` 類型的 `ldexp` 的多載。  在 C 程式中，`ldexp` 會一律採用 `double` 和 `int` 並傳回 `double`。  
  
## 需求  
  
|常式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`ldexp`, `ldexpf`, `ldexpl`|\<math.h\>|\<cmath\>|  
  
 如需相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_ldexp.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 4.0, y;  
   int p = 3;  
  
   y = ldexp( x, p );  
   printf( "%2.1f times two to the power of %d is %2.1f\n", x, p, y );  
}  
```  
  
## 輸出  
  
```  
4.0 times two to the power of 3 is 32.0  
```  
  
## .NET Framework 對等用法  
 [System::Math::Pow](https://msdn.microsoft.com/en-us/library/system.math.pow.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)   
 [modf、 modff modfl](../../c-runtime-library/reference/modf-modff-modfl.md)