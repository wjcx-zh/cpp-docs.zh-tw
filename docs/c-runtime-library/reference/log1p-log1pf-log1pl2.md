---
title: "log1p log1pf log1pl | Microsoft Docs"
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
  - "log1p"
  - "log1pf"
  - "log1pl"
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
  - "log1p"
  - "log1pf"
  - "log1pl"
  - "math/log1p"
  - "math/log1pf"
  - "math/log1pl"
helpviewer_keywords: 
  - "log1p 函式"
  - "log1pf 函式"
  - "log1pl 函式"
ms.assetid: a40d965d-b4f6-42f4-ba27-2395546f7c12
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# log1p log1pf log1pl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算自然對數 1 再加上指定的值。  
  
## 語法  
  
```  
double log1p(  
   double x  
);  
  
float log1p(  
   float x  
); //C++ only  
  
long double log1p(  
   long double x  
); //C++ only  
  
float log1pf(  
   float x  
);  
  
long double log1pl(  
   long double x  
);  
  
```  
  
#### 參數  
 `x`  
 浮點的引數。  
  
## 傳回值  
 如果成功，傳回的自然 \(以 e 為底數\) 對數 \(`x`\+ 1\)。  
  
 否則，可能會傳回下列值之一︰  
  
|輸入|結果|SEH 例外狀況|errno|  
|--------|--------|--------------|-----------|  
|inf \+|inf \+|||  
|非正規數|與輸入相同|反向溢位||  
|±0|與輸入相同|||  
|\-1|\-inf|DIVBYZERO|ERANGE|  
|\< \-1|nan|不正確|EDOM|  
|\-inf|nan|不正確|EDOM|  
|±SNaN|與輸入相同|不正確||  
|無限期 ±QNaN|與輸入相同|||  
  
 `errno` 如果值設為 ERANGE `x` \=\-1。`errno` 如果值設為 EDOM `x` \< − 1。  
  
## 備註  
 `log1p` 函式可能比使用記錄檔更準確 \(`x`\+ 1\) x 時趨近於 0。  
  
 因為 c \+ \+ 允許多載，所以您可以呼叫的多載 `log1p` 採用並傳回浮點和長雙精度浮點型別。 在 C 程式中， `log1p` 一律採用並傳回雙精度浮點數。  
  
 如果 `x` 是自然的數字，此函式傳回的對數字的階乘 \(`x`\-1\)。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`log1p`, `log1pf`,  `log1pl`|\<math.h\>|\<cmath\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [log2 log2f log2l](../../c-runtime-library/reference/log2-log2f-log2l.md)   
 [log、logf、log10、log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)