---
title: "remainder、remainderf、remainderl | Microsoft Docs"
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
  - "remainderl"
  - "remainder"
  - "remainderf"
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
  - "remainderf"
  - "remainder"
  - "remainderl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remainderf"
  - "remainderl"
  - "餘數"
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
caps.latest.revision: 8
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# remainder、remainderf、remainderl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算兩個浮點數值商數的其餘部分，會四捨五入至最接近的整數值。  
  
## 語法  
  
```  
double remainder(   
   double numer,  
   double denom  
);  
float remainder(   
   float numer,  
   float denom  
); /* C++ only */  
long double remainder(   
   long double numer,  
   long double denom  
); /* C++ only */  
float remainderf(   
   float numer,  
   float denom  
);  
long double remainderl(   
   long double numer,  
   long double denom  
);  
  
```  
  
#### 參數  
 `numer`  
 分子。  
  
 `denom`  
 分母。  
  
## 傳回值  
 `x` \/ `y`浮點數餘數。  如果 `y` 的值為 0.0，`remainder` 就會傳回無訊息 NaN。  如需以 `printf` 系列表示無訊息 NaN 的詳細資訊，請參閱 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)。  
  
## 備註  
 `remainder`函式會計算浮點數餘數`r``x` \/ `y`像是`x` \= `n` \* `y` \+ `r`，`n` 是最接近`x` \/ `y`的值，`n`是偶數無論是否整除 `n`。 \- `x` \/ `y` &#124; \= 1\/2.  當 `r` \= 0， `r` 有與 `x`相同的標記。  
  
 因為 C\+\+ 允許多載，您可以呼叫會接受並傳回 `float` 或 `long double` 值的 `remainder` 多載。  在 C 程式中， `remainder` 一律接受並傳回雙精確度浮點數。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`remainder`, `remainderf`, `remainderl`|\<math.h\>|  
  
 如需相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```c  
// crt_remainder.c  
// This program displays a floating-point remainder.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double w = -10.0, x = 3.0, z;  
  
   z = remainder(w, x);  
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);  
}  
```  
  
  **\-10.00 \/ 3.00 的餘數為 \-1.000000**   
## .NET Framework 對等用法  
 [System::Math::IEEERemainder](https://msdn.microsoft.com/en-us/library/system.math.ieeeremainder.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [ldiv、lldiv](../../c-runtime-library/reference/ldiv-lldiv.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)   
 [fmod、fmodf](../../c-runtime-library/reference/fmod-fmodf.md)   
 [remquo、remquof、remquol](../../c-runtime-library/reference/remquo-remquof-remquol.md)