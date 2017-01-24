---
title: "fmod、fmodf | Microsoft Docs"
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
  - "fmod"
  - "fmodf"
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
  - "fmod"
  - "_fmodl"
  - "fmodf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "計算浮點數餘數"
  - "fmodf 函式"
  - "fmod 函式"
  - "浮點數，計算餘數"
ms.assetid: 6962d369-d11f-40b1-a6d7-6f67239f8a23
caps.latest.revision: 13
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fmod、fmodf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算浮點數餘數。  
  
## 語法  
  
```  
double fmod(   
   double x,  
   double y   
);  
float fmod(  
   float x,  
   float y   
);  // C++ only  
long double fmod(  
   long double x,  
   long double y  
);  // C++ only  
float fmodf(   
   float x,  
   float y   
);  
```  
  
#### 參數  
 `x`, `y`  
 浮點數的值。  
  
## 傳回值  
 `fmod` 會傳回 `x` \/ `y` 的浮點數餘數。  如果 `y` 的值為 0.0，`fmod` 就會傳回無訊息 NaN。  如需以 `printf` 系列表示無訊息 NaN 的詳細資訊，請參閱 [](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md "printf, _printf_l, wprintf, _wprintf_l")。  
  
## 備註  
 `fmod` 函式計算 `x` \/ `y` 的浮點數餘數 `f`，將此餘數代入 `x` \= `i` `*` `y` \+ `f`，其中 `i` 為整數，`f` 的正負號與 `x` 相同，並且 `f` 的絕對值小於 `y` 的絕對值。  
  
 C\+\+ 允許多載，因此您可以呼叫 `fmod` 不同版本的多載。  在 C 程式中， `fmod` 一律接受並傳回雙精確度浮點數。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`fmod`, `fmodf`|\<math.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_fmod.c  
// This program displays a floating-point remainder.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double w = -10.0, x = 3.0, z;  
  
   z = fmod( w, x );  
   printf( "The remainder of %.2f / %.2f is %f\n", w, x, z );  
}  
```  
  
  **\-10.00 \/ 3.00 的餘數為 \-1.000000**   
## .NET Framework 對等用法  
 [System::Math::IEEERemainder](https://msdn.microsoft.com/en-us/library/system.math.ieeeremainder.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [ceil、ceilf、ceill](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [fabs、 fabsf fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [floor、floorf、floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [\_CIfmod](../../c-runtime-library/cifmod.md)