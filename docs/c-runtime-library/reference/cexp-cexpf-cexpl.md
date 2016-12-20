---
title: "cexp、cexpf、cexpl | Microsoft Docs"
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
  - "cexp"
  - "cexpf"
  - "cexpl"
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
  - "cexp"
  - "cexpf"
  - "cexpl"
  - "complex/cepx"
  - "complex/cexpf"
  - "complex/cexpl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "cexp 函式"
  - "cexpl 函式"
  - "cexpf 函式"
ms.assetid: f27fd5a9-70c7-4957-a7ee-5256d19bd1da
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# cexp、cexpf、cexpl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算底數為 e 之複數的指數。  
  
## 語法  
  
```  
_Dcomplex cexp(   
   _Dcomplex z   
);  
_Fcomplex cexp(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex cexp(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex cexpf(   
  _Fcomplex z   
);  
_Lcomplex cexpl(   
   _Lcomplex z   
);  
```  
  
#### 參數  
 `z`  
 代表指數的複數。  
  
## 傳回值  
 `e` 的值為 `z` 的乘冪。  
  
## 備註  
 因為 C\+\+ 允許多載，所以您可以呼叫採用並傳回 `cexp` 和 `_Fcomplex` 值的 `_Lcomplex` 的多載。 在 C 程式中，`cexp` 會一律採用及傳回 `_Dcomplex`。  
  
## 需求  
  
|常式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`cexp`, `cexpf`, `cexpl`|\<complex.h\>|\<complex.h\>|  
  
 如需相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [cpow cpowf cpowl](../../c-runtime-library/reference/cpow-cpowf-cpowl.md)   
 [clog10 clog10f clog10l](../../c-runtime-library/reference/clog10-clog10f-clog10l.md)   
 [clog、 clogf、 clogl](../../c-runtime-library/reference/clog-clogf-clogl.md)