---
title: "remquo、remquof、remquol | Microsoft Docs"
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
  - "remquof"
  - "remquo"
  - "remquol"
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
  - "remquof"
  - "remquol"
  - "remquo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remquol 函式"
  - "remquof 函式"
  - "remquo 函式"
ms.assetid: a1d3cb8b-8027-4cd3-8deb-04eb17f299fc
caps.latest.revision: 8
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# remquo、remquof、remquol
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算兩個整數值的餘數，並將帶正負號的整數值和商數的近似強度儲存在參數中指定的位置。  
  
## 語法  
  
```  
double remquo(   
   double numer,  
   double denom,  
   int* quo  
);  
float remquo(   
   float numer,  
   float denom,  
   int* quo  
); /* C++ only */  
long double remquo(   
   long double numer,  
   long double denom,  
   int* quo  
); /* C++ only */  
float remquof(   
   float numer,  
   float denom,  
   int* quo  
);  
long double remquol(   
   long double numer,  
   long double denom,  
   int* quo  
);  
  
```  
  
#### 參數  
 `numer`  
 分子。  
  
 `denom`  
 分母。  
  
 `quo`  
 整數指標，用於儲存商數標記和大約範圍的值。  
  
## 傳回值  
 `remquo` 會傳回 `x` \/ `y` 的浮點數餘數。  如果 `y` 的值為 0.0，`remquo` 就會傳回無訊息 NaN。  如需以 `printf` 系列表示無訊息 NaN 的詳細資訊，請參閱 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)。  
  
## 備註  
 `remquo` 函式計算 `x` \/ `y` 的浮點數餘數 `f`，將此餘數代入 `x` \= `i` `*` `y` \+ `f`，其中 `i` 為整數，`f` 的正負號與 `x` 相同，並且 `f` 的絕對值小於 `y` 的絕對值。  
  
 C\+\+ 允許多載，因此您可以呼叫會接受並傳回 `float` 或 `long double` 值的 `remquo` 多載。  在 C 程式中， `remquo` 一律接受並傳回雙精確度浮點數。  
  
## 需求  
  
|Function|必要的標頭|  
|--------------|-----------|  
|`remquo`, `remquof`, `remquol`|\<math.h\>|  
  
 如需相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```c  
// crt_remquo.c  
// This program displays a floating-point remainder.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double w = -10.0, x = 3.0, z;  
   int quo = 0;  
  
   z = remquo(w, x, &quo);  
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);  
   printf("Approximate signed quotient is %d\n", quo);  
}  
```  
  
  **\-10.00 \/ 3.00 的餘數為 \-1.000000**  
**近似帶正負號的商數是 \-3**   
## .NET Framework 對等用法  
 [System::Math::IEEERemainder](https://msdn.microsoft.com/en-us/library/system.math.ieeeremainder.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [ldiv、lldiv](../../c-runtime-library/reference/ldiv-lldiv.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)   
 [fmod、fmodf](../../c-runtime-library/reference/fmod-fmodf.md)   
 [remainder、remainderf、remainderl](../../c-runtime-library/reference/remainder-remainderf-remainderl.md)