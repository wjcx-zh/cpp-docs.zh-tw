---
title: "sqrt、sqrtf、sqrtl | Microsoft Docs"
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
  - "sqrtl"
  - "sqrtf"
  - "sqrt"
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
  - "sqrt"
  - "sqrtf"
  - "_sqrtl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_sqrtl 函式"
  - "計算平方根"
  - "sqrt 函式"
  - "sqrtf 函式"
  - "sqrtl 函式"
  - "平方根, 計算"
ms.assetid: 2ba9467b-f172-41dc-8f10-b86f68fa813c
caps.latest.revision: 18
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# sqrt、sqrtf、sqrtl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算平方根。  
  
## 語法  
  
```  
double sqrt(    double x  ); float sqrt(    float x  );  // C++ only long double sqrt(    long double x );  // C++ only float sqrtf(    float x  ); long double sqrtl(    long double x  );  
```  
  
#### 參數  
 `x`  
 非負值浮點值  
  
## 備註  
 因為 C\+\+ 允許多載，所以您可以呼叫採用 `float` 和 `long double` 類型的 `sqrt` 的多載。  在 C 程式中，`sqrt` 會一律採用並傳回 `double`。  
  
## 傳回值  
 `sqrt` 函式會傳回 `x` 的平方根。  根據預設，若 `x` 為負值，`sqrt` 會傳回不確定的 NaN。  
  
|輸入|SEH 例外狀況|`_matherr` 例外狀況|  
|--------|--------------|---------------------|  
|± QNAN、IND|無|\_DOMAIN|  
|\- ∞|無|\_DOMAIN|  
|x\<0|無|\_DOMAIN|  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`sqrt`, `sqrtf`, `sqrtl`|\<math.h\>|\<cmath\>|  
  
 如需相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_sqrt.c  
// This program calculates a square root.  
  
#include <math.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   double question = 45.35, answer;  
   answer = sqrt( question );  
   if( question < 0 )  
      printf( "Error: sqrt returns %f\n", answer );  
   else  
      printf( "The square root of %.2f is %.2f\n", question, answer );  
}  
```  
  
  **45.35 的平方根是 6.73**   
## .NET Framework 對等用法  
 [System::Math::Sqrt](https://msdn.microsoft.com/en-us/library/system.math.sqrt.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [exp、expf](../../c-runtime-library/reference/exp-expf.md)   
 [log、logf、log10、log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)   
 [pow、powf、powl](../../c-runtime-library/reference/pow-powf-powl.md)   
 [\_CIsqrt](../../c-runtime-library/cisqrt.md)