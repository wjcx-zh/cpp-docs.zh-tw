---
title: "clog10 clog10f clog10l | Microsoft Docs"
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
  - "clog10"
  - "clog10f"
  - "clog10l"
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
  - "clog10"
  - "clog10f"
  - "clog10l"
  - "complex/clog10"
  - "complex/clog10f"
  - "complex/clog10l"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "clog10 函式"
  - "clog10f 函式"
  - "clog10l 函式"
ms.assetid: 2ddae00d-ef93-4441-add3-f4d58358401b
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# clog10 clog10f clog10l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取複數的基底 10 對數。  
  
## 語法  
  
```  
_Dcomplex clog10(   
   _Dcomplex z   
);  
_Fcomplex clog10(   
  _Fcomplex z   
);  // C++ only  
_Lcomplex clog10(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex clog10f(   
   _Fcomplex z   
);  
_Lcomplex clog10l(   
   _Lcomplex z   
);  
```  
  
#### 參數  
 `z`  
 對數的底數。  
  
## 傳回值  
 可能的傳回值如下︰  
  
|z 參數|傳回值|  
|----------|---------|  
|正|Z 基底 10 對數。|  
|零|\- ∞|  
|負|NaN|  
|NaN|NaN|  
|\+ ∞|\+ ∞|  
  
## 備註  
 因為 C\+\+ 允許多載，所以您可以呼叫採用並傳回 `clog10` 和 `_Fcomplex` 值的 `_Lcomplex` 的多載。 在 C 程式中， `clog10` 一律採用並傳回 `_Dcomplex` 值。  
  
## 需求  
  
|常式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`clog10`, `clog10f`, `clogl`|\<complex.h\>|\< x \>|  
  
 如需相容性詳細資訊，請參閱簡介中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [cexp、cexpf、cexpl](../../c-runtime-library/reference/cexp-cexpf-cexpl.md)   
 [cpow cpowf cpowl](../../c-runtime-library/reference/cpow-cpowf-cpowl.md)   
 [clog、 clogf、 clogl](../../c-runtime-library/reference/clog-clogf-clogl.md)