---
title: "ilogb、 ilogbf、 ilogbl | Microsoft Docs"
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
  - "ilogb"
  - "ilogbf"
  - "ilogbl"
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
  - "ilogb"
  - "ilogbf"
  - "ilogbl"
  - "math/ilogb"
  - "math/ilogbf"
  - "math/ilogbl"
helpviewer_keywords: 
  - "ilogb 函式"
  - "ilogbf 函式"
  - "ilogbl 函式"
ms.assetid: 9ef19d57-1caa-41d5-8233-2faad3562fcb
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ilogb、 ilogbf、 ilogbl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取表示指定值的非偏誤的基底 2 指數的整數。  
  
## 語法  
  
```  
int ilogb(  
   double x  
);  
  
int ilogb(  
   float x  
); //C++ only  
  
int ilogb(  
   long double x  
); //C++ only  
  
int ilogbf(  
   float x  
);  
  
int ilogbl(  
   long double x  
);  
  
```  
  
#### 參數  
 \[in\] `x`  
 指定值。  
  
## 傳回值  
 如果成功，傳回的基底 2 指數 `x` 為帶正負號 `int` 值。  
  
 否則，傳回下列值，在 \< h.h \> 中定義的其中一個︰  
  
|輸入|結果|  
|--------|--------|  
|±0|FP\_ILOGB0|  
|±inf，±nan，無限期|FP\_ILOGBNAN|  
  
 錯誤報告中所指定 [\_matherr](../../c-runtime-library/reference/matherr.md)。  
  
## 備註  
 因為 c \+ \+ 允許多載，所以您可以呼叫的多載 `ilogb` 採用並傳回浮點和長雙精度浮點型別。 在 C 程式中， `ilogb` 一律採用並傳回雙精度浮點數。  
  
 呼叫此函式是類似於呼叫的對應 `logb` 函式，則傳回值轉換成 `int`。  
  
## 需求  
  
|常式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`ilogb`, `ilogbf`,  `ilogbl`|\<math.h\>|\<cmath\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)   
 [logb、logbf、logbl、\_logb、\_logbf](../../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)