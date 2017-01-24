---
title: "exp2、 exp2f、 exp2l | Microsoft Docs"
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
  - "exp2"
  - "exp2f"
  - "exp2l"
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
  - "exp2"
  - "math/exp2"
  - "exp2f"
  - "math/exp2f"
  - "exp2l"
  - "math/exp2l"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "exp2 函式"
  - "exp2f 函式"
  - "exp2l 函式"
ms.assetid: 526e3e10-201a-4610-a886-533f44ece344
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# exp2、 exp2f、 exp2l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算指定的值 \(亦即，2ˣ\) 2。  
  
## 語法  
  
```  
double exp2(  
   double x  
);  
  
float exp2(  
   float x  
);  // C++ only  
  
long double exp2(  
   long double x  
); // C++ only  
  
float exp2f(  
   float x  
);  
  
long double exp2l(  
   long double x  
);  
  
```  
  
#### 參數  
 \[in\] `x`  
 指數值。  
  
## 傳回值  
 如果成功，傳回的基底 2 指數 `x` \(2ˣ\)。 否則，可能會傳回下列值之一︰  
  
|問題|返回|  
|--------|--------|  
|`x` \= ±0|1|  
|`x` \=\-INFINITY|\+0|  
|`x` \= \+ INFINITY|\+ INFINITY|  
|`x` \= NaN|NaN|  
|溢位範圍錯誤|\+ HUGE\_VAL、 \+ HUGE\_VALF，或 \+ HUGE\_VALL|  
|反向溢位範圍錯誤|正確的結果，四捨五入之後|  
  
 錯誤報告中所指定 [\_matherr](../../c-runtime-library/reference/matherr.md)。  
  
## 備註  
 因為 c \+ \+ 允許多載，所以您可以呼叫的多載 `exp2` 採用並傳回浮點和長雙精度浮點型別。 在 C 程式中， `exp2` 一律採用並傳回雙精度浮點數。  
  
## 需求  
  
|常式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`exp`, `expf`, `expl`|\<math.h\>|\<cmath\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [exp、expf](../../c-runtime-library/reference/exp-expf.md)   
 [log2 log2f log2l](../../c-runtime-library/reference/log2-log2f-log2l.md)