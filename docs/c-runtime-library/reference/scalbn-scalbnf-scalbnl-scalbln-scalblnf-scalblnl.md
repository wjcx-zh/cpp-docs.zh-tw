---
title: "scalbn、scalbnf、scalbnl、scalbln、scalblnf、scalblnl | Microsoft Docs"
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
  - "scalblnl"
  - "scalbnl"
  - "scalbnf"
  - "scalblnf"
  - "scalbn"
  - "scalbln"
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
  - "scalblnf"
  - "scalbnl"
  - "scalblnl"
  - "scalbln"
  - "scalbn"
  - "scalbnf"
dev_langs: 
  - "C++"
ms.assetid: df2f1543-8e39-4af4-a5cf-29307e64807d
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# scalbn、scalbnf、scalbnl、scalbln、scalblnf、scalblnl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將浮點數與 FLT\_RADIX 的整數冪相乘。  
  
## 語法  
  
```  
double scalbn(    double x,    int exp  ); float scalbn(    float x,    int exp );  // C++ only long double scalbn(    long double x,    int exp );  // C++ only  float scalbnf(    float x,    int exp );  long double scalbnl(    long double x,    int exp ); double scalbln(    double x,    long exp  ); float scalbln(    float x,    long exp );  // C++ only long double scalbln(    long double x,    long exp );  // C++ only  float scalblnf(    float x,    long exp );  long double scalblnl(    long double x,    long exp );  
```  
  
#### 參數  
 `x`  
 浮點值。  
  
 `exp`  
 整數指數。  
  
## 傳回值  
 若成功，`scalbn` 函數會傳回 `x` \* `FLT_RADIX`<sup>exp</sup> 的值。  溢位 \(根據 `x` 的符號\) 時，`scalbn` 會傳回 \+\/– `HUGE_VAL`；`errno` 值會設為 `ERANGE`。  
  
 如需有關 `errno` 和其他可能的錯誤傳回值的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `FLT_RADIX` 定義在 \<float.h\> 作為原生浮點基數；在二進位系統中，其具有 2 的值，且 `scalbn` 相當於 [ldexp](../../c-runtime-library/reference/ldexp.md)。  
  
 因為 C\+\+ 允許多載，所以您可以呼叫採用並傳回 `float` 或 `long double` 類型的 `scalbn` 和 `scalbln` 的多載。  在 C 程式中，`scalbn` 會一律採用 `double` 及 `int`，並傳回 `double`，而 `scalbln` 會一律採用 `double` 及 `long`，並傳回 `double`。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`scalbn`, `scalbnf`, `scalbnl`, `scalbln`, `scalblnf`, `scalblnl`|\<math.h\>|\<cmath\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_scalbn.c  
// Compile using: cl /W4 crt_scalbn.c  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 6.4, y;  
   int p = 3;  
  
   y = scalbn( x, p );  
   printf( "%2.1f times FLT_RADIX to the power of %d is %2.1f\n", x, p, y );  
}  
```  
  
## 輸出  
  
```  
6.4 times FLT_RADIX to the power of 3 is 51.2  
```  
  
## .NET Framework 對等用法  
 [System::Math::Pow](https://msdn.microsoft.com/en-us/library/system.math.pow.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)   
 [ldexp](../../c-runtime-library/reference/ldexp.md)   
 [modf、 modff modfl](../../c-runtime-library/reference/modf-modff-modfl.md)