---
title: "fmax、 fmaxf、 fmaxl | Microsoft Docs"
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
  - "fmax"
  - "fmaxf"
  - "fmaxl"
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
  - "fmax"
  - "fmaxf"
  - "fmaxl"
  - "math/fmax"
  - "math/fmaxf"
  - "math/fmaxl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "fmax 函式"
  - "fmaxf 函式"
  - "fmaxl 函式"
ms.assetid: a773ccf7-495e-4a9a-8c6d-dfb53e341e35
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fmax、 fmaxf、 fmaxl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

決定使用較大的兩個指定的數值。  
  
## 語法  
  
```  
double fmax(  
   double x,   
   double y  
);  
  
float fmax(  
   float x,   
   float y  
); //C++ only  
  
long double fmax(  
   long double x,   
   long double y  
); //C++ only  
  
float fmaxf(  
   float x,   
   float y  
);  
  
long double fmaxl(  
   long double x,   
   long double y  
);  
  
```  
  
#### 參數  
 \[in\] `x`  
 要比較的第一個值。  
  
 \[in\] `y`  
 要比較的第二個值。  
  
## 傳回值  
 如果成功，傳回較大的 `x` 或 `y`。 傳回的值是精確的而不需依賴任何形式的捨入。  
  
 否則，可能會傳回下列值之一︰  
  
|問題|返回|  
|--------|--------|  
|`x` \= NaN|`y`|  
|`y` \= NaN|`x`|  
|`x` 和 `y` \= NaN|NaN|  
  
 此函式不會使用指定的錯誤  [\_matherr](../../c-runtime-library/reference/matherr.md)。  
  
## 備註  
 因為 c \+ \+ 允許多載，所以您可以呼叫多的載 fmax 採用並傳回浮點和長雙精度浮點型別。 在 C 程式中，fmax 一律採用並傳回雙精度浮點數。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`fmax`, `fmaxf`, `fmaxl`|\<math.h\>|\<cmath\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fmin, fminf, fminl](../Topic/fmin,%20fminf,%20fminl1.md)