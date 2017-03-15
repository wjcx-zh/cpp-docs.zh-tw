---
title: "tgamma、 tgammaf、 tgammal | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "tgamma"
  - "tgammaf"
  - "tgammal"
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
  - "tgamma"
  - "tgammaf"
  - "tgammal"
  - "math/tgamma"
  - "math/tgammaf"
  - "math/tgammal"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tgamma 函式"
  - "tgammaf 函式"
  - "tgammal 函式"
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# tgamma、 tgammaf、 tgammal
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷指定的值的 gamma 函式。  
  
## 語法  
  
```  
double tgamma(  
   double x  
);  
  
float tgamma(  
   float x  
); //C++ only  
  
long double tgamma(  
   long double x  
); //C++ only  
  
float tgammaf(  
   float x  
);  
  
long double tgammal(  
   long double x  
);  
  
```  
  
#### 參數  
 \[in\] `x`  
 若要尋找的 gamma 值。  
  
## 傳回值  
 如果成功，傳回的 gamma `x`。  
  
 如果可能發生範圍錯誤的嚴重性 `x` 太大或太小，資料類型。 如果可能發生網域錯誤或範圍錯誤 `x` \< \= 0。  
  
|問題|返回|  
|--------|--------|  
|x \= ±0|±INFINITY|  
|x \= 負整數|NaN|  
|x \=\-INFINITY|NaN|  
|x \= \+ INFINITY|\+ INFINITY|  
|x \= NaN|NaN|  
|網域錯誤|NaN|  
|柵欄錯誤|±HUGE\_VAL、 ±HUGE\_VALF 或 ±HUGE\_VALL|  
|溢位範圍錯誤|±HUGE\_VAL、 ±HUGE\_VALF 或 ±HUGE\_VALL|  
|反向溢位範圍錯誤|四捨五入後的正確值。|  
  
 錯誤報告中所指定 [\_matherr](../../c-runtime-library/reference/matherr.md)。  
  
## 備註  
 因為 c \+ \+ 允許多載，所以您可以呼叫多的載 tgamma 採用並傳回浮點和長雙精度浮點型別。 在 C 程式中，tgamma 一律採用並傳回雙精度浮點數。  
  
 如果 x 是自然的數字，此函數會傳回 \(x\-1\) 的階乘。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`tgamma`, `tgammaf`,  `tgammal`|\<math.h\>|\<cmath\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [lgamma、 lgammaf、 lgammal](../../c-runtime-library/reference/lgamma-lgammaf-lgammal.md)