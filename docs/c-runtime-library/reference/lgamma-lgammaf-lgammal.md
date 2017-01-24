---
title: "lgamma、 lgammaf、 lgammal | Microsoft Docs"
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
  - "lgamma"
  - "lgammaf"
  - "lgammal"
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
  - "lgamma"
  - "lgammaf"
  - "lgammal"
  - "math/lgamma"
  - "math/lgammaf"
  - "math/lgammal"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "lgamma 函式"
  - "lgammal 函式"
  - "lgammaf 函式"
ms.assetid: 6e326c58-7077-481a-a329-c82ae56ae9e6
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# lgamma、 lgammaf、 lgammal
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷指定值的 gamma 函數的絕對值的自然對數。  
  
## 語法  
  
```  
double lgamma(  
   double x  
);  
  
float lgamma(  
   float x  
); //C++ only  
  
long double lgamma(  
   long double x  
); //C++ only  
  
float lgammaf(  
   float x  
);  
  
long double lgammal(  
   long double x  
);  
  
```  
  
#### 參數  
 \[in\] `x`  
 要計算的值。  
  
## 傳回值  
 如果成功，傳回 gamma 函數的絕對值的自然對數 `x.`  
  
|問題|返回|  
|--------|--------|  
|`x` \= NaN|NaN|  
|`x` \= ±0|\+ INFINITY|  
|`x`\= 負整數|\+ INFINITY|  
|±INFINITY|\+ INFINITY|  
|柵欄錯誤|\+ HUGE\_VAL、 \+ HUGE\_VALF，或 \+ HUGE\_VALL|  
|溢位範圍錯誤|±HUGE\_VAL、 ±HUGE\_VALF 或 ±HUGE\_VALL|  
  
 錯誤報告中所指定 [\_matherr](../../c-runtime-library/reference/matherr.md)。  
  
## 備註  
 因為 c \+ \+ 允許多載，所以您可以呼叫的多載 `lgamma` 採用並傳回浮點和長雙精度浮點型別。 在 C 程式中， `lgamma` 一律採用並傳回雙精度浮點數。  
  
 如果 x 有理數，此函數會傳回的對數字的階乘 \(`x`\-1\)。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`lgamma`, `lgammaf`,  `lgammal`|\<math.h\>|\<cmath\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [tgamma、 tgammaf、 tgammal](../../c-runtime-library/reference/tgamma-tgammaf-tgammal.md)