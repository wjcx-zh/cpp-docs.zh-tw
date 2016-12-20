---
title: "fma、 fmaf、 fmal | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fma"
  - "fmaf"
  - "fmal"
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
  - "fma"
  - "fmaf"
  - "fmal"
  - "math/fma"
  - "math/fmaf"
  - "math/fmal"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "fma 函式"
  - "fmaf 函式"
  - "fmal 函式"
ms.assetid: 584a6037-da1e-4e86-9f0c-97aae86de0c0
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fma、 fmaf、 fmal
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將兩個值一起相乘，新增第三個值，並接著會將結果，而不會遺失任何因為中間的四捨五入的精確度。  
  
## 語法  
  
```  
double fma(  
   double x,   
   double y,   
   double z  
);  
  
float fma(  
   float  x,   
   float  y,   
   float z  
); //C++ only  
  
long double fma(  
   long double  x,   
   long double  y,   
   long double z  
); //C++ only  
  
float fmaf(  
   float  x,   
   float  y,   
   float z  
);  
  
long double fmal(  
   long double  x,   
   long double  y,   
   long double z  
);  
  
```  
  
#### 參數  
 \[in\] `x`  
 要相乘的第一個值。  
  
 \[in\] `y`  
 要相乘的第二個值。  
  
 \[in\] `z`  
 要加入的值。  
  
## 傳回值  
 Returns \(`x` ×    `y`\) \+ `z`. 傳回值就是使用目前的捨入格式會四捨五入。  
  
 否則，可能會傳回下列值之一︰  
  
|問題|返回|  
|--------|--------|  
|`x` \= 無限大， `y` \= 0 或<br /><br /> `x` \= 0， `y` \= 無限|NaN|  
|`x` 或 `y` \= 確切 ± 無限大， `z` \= 無限正負號相反|NaN|  
|`x` 或 `y` \= NaN|NaN|  
|不 \(`x` \= 0， `y`\= 無限期\) 和 `z` \= NaN<br /><br /> 不 \(`x`\= 無限期， `y`\= 0\) 和 `z` \= NaN|NaN|  
|溢位範圍錯誤|±HUGE\_VAL、 ±HUGE\_VALF 或 ±HUGE\_VALL|  
|反向溢位範圍錯誤|正確的值之後捨入。|  
  
 錯誤報告中所指定 [\_matherr](../../c-runtime-library/reference/matherr.md)。  
  
## 備註  
 因為 c \+ \+ 允許多載，所以您可以呼叫的多載 `fma` 採用並傳回浮點和長雙精度浮點型別。 在 C 程式中， `fma` 一律採用並傳回雙精度浮點數。  
  
 此函式計算的值，就好像它拍攝無限的有效位數，並接著會將最後的結果。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`fma`, `fmaf`,  `fmal`|\<math.h\>|\<cmath\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [remainder、remainderf、remainderl](../../c-runtime-library/reference/remainder-remainderf-remainderl.md)   
 [remquo、remquof、remquol](../../c-runtime-library/reference/remquo-remquof-remquol.md)