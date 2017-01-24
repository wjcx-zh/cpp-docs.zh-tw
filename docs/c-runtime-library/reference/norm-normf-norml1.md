---
title: "norm、 normf norml | Microsoft Docs"
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
  - "norm"
  - "normf"
  - "norml"
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
  - "norm"
  - "normf"
  - "norml"
  - "complex/norm"
  - "complex/normf"
  - "complex/norml"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "norm 函式"
  - "normf 函式"
  - "norml 函式"
ms.assetid: 9786ecfe-0019-4553-b378-0af6c691e15c
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# norm、 normf norml
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取複數的平方誤差大小。  
  
## 語法  
  
```  
double norm(   
   _Dcomplex z   
);  
float norm(   
   _Fcomplex z   
);  // C++ only  
long double norm(   
  _Lcomplex z   
);  // C++ only  
float normf(   
   _Fcomplex z   
);  
long double norml(   
   _Lcomplex z   
);  
```  
  
#### 參數  
 `z`  
 複數。  
  
## 傳回值  
 平方的大小 `z`。  
  
## 備註  
 因為 c \+ \+ 允許多載，所以您可以呼叫的多載 `norm` 採用 `_Fcomplex` 或 `_Lcomplex` 值，並傳回 `float` 或 `long double` 值。 在 C 程式中， `norm` 一律採用 `_Dcomplex` 值並傳回 `double` 值。  
  
## 需求  
  
|常式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`norm`, `normf`, `norml`|\<complex.h\>|\< x \>|  
  
 如需相容性詳細資訊，請參閱簡介中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [creal crealf creall](../../c-runtime-library/reference/creal-crealf-creall.md)   
 [cproj cprojf cprojl](../../c-runtime-library/reference/cproj-cprojf-cprojl.md)   
 [conj conjf conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)   
 [cimag cimagf cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)   
 [carg cargf cargl](../../c-runtime-library/reference/carg-cargf-cargl.md)   
 [封包，cabsf cabsl](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)