---
title: "fdim、 fdimf、 fdiml | Microsoft Docs"
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
  - "fdim"
  - "fdimf"
  - "fdiml"
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
  - "fdim"
  - "fdimf"
  - "fdiml"
  - "math/fdim"
  - "math/fdimf"
  - "math/fdiml"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "fdim 函式"
  - "fdimf 函式"
  - "fdiml 函式"
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fdim、 fdimf、 fdiml
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷第一個和第二個值之間的正面效果。  
  
## 語法  
  
```  
double fdim(  
   double x,   
   double y  
);  
  
float fdim(  
   float x,   
   float y  
); //C++ only  
  
long double fdim(  
   long double x,   
   long double y  
); //C++ only  
  
float fdimf(  
   float x,   
   float y  
);  
  
long double fdiml(  
   long double x,   
   long double y  
);  
  
```  
  
#### 參數  
 \[in\] `x`  
 第一個值。  
  
 \[in\] `y`  
 第二個值。  
  
## 傳回值  
 傳回正數差異 `x` 和 `y`:  
  
|傳回值|情節|  
|---------|--------|  
|x y|如果 x \> y|  
|0|如果 x \< \= y|  
  
 否則，可能會傳回下列錯誤︰  
  
|問題|返回|  
|--------|--------|  
|溢位範圍錯誤|\+ HUGE\_VAL、 \+ HUGE\_VALF，或 \+ HUGE\_VALL|  
|反向溢位範圍錯誤|正確的值 （之後捨入）|  
|`x` 或 `y` 是 NaN|NaN|  
  
 錯誤報告中所指定 [\_matherr](../../c-runtime-library/reference/matherr.md)。  
  
## 備註  
 因為 c \+ \+ 允許多載，所以您可以呼叫的多載 `fdim` 採用並傳回浮點和長雙精度浮點型別。 在 C 程式中， `fdim` 一律採用並傳回雙精度浮點數。  
  
 除了 NaN 處理中，此函式相當於 [fmax、 fmaxf、 fmaxl](../../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)\(`x`\-`y,` 0\)。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`fdim`, `fdimf`,  `fdiml`|\<math.h\>|\<cmath\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fmax、 fmaxf、 fmaxl](../../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)   
 [abs、 實驗室、 llabs、 \_abs64](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)