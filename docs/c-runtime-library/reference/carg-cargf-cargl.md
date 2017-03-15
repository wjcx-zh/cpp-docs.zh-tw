---
title: "carg cargf cargl | Microsoft Docs"
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
  - "carg"
  - "cargf"
  - "cargl"
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
  - "carg"
  - "cargf"
  - "cargl"
  - "complex/carg"
  - "complex/cargf"
  - "complex/cargl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "carg 函式"
  - "cargf 函式"
  - "cargl 函式"
ms.assetid: 610d6a93-b929-46ab-a966-b77db0b804be
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# carg cargf cargl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

與分支沿著負真實軸擷取複雜數字的引數。  
  
## 語法  
  
```  
double carg(   
   _Dcomplex z   
);  
float carg(   
   _Fcomplex z   
);  // C++ only  
long double carg(   
   _Lcomplex z   
);  // C++ only  
float cargf(   
   _Fcomplex z   
);  
long double cargl(   
   _Lcomplex z   
);  
```  
  
#### 參數  
 `z`  
 複數。  
  
## 傳回值  
 引數 （亦稱為階段） 的 `z`。 結果是 \[−π，\+ π\] 間隔。  
  
## 備註  
 因為 c \+ \+ 允許多載，所以您可以呼叫的多載 `carg` 採用 `_Fcomplex` 或 `_Lcomplex` 值，並傳回 `float` 或 `long double` 值。 在 C 程式中， `carg` 一律採用 `_Dcomplex` 值並傳回 `double` 值。  
  
## 需求  
  
|常式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`carg`, `cargf`, `cargl`|\<complex.h\>|\< x \>|  
  
 如需相容性詳細資訊，請參閱簡介中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [norm、 normf norml](../../c-runtime-library/reference/norm-normf-norml1.md)   
 [creal crealf creall](../../c-runtime-library/reference/creal-crealf-creall.md)   
 [cproj cprojf cprojl](../../c-runtime-library/reference/cproj-cprojf-cprojl.md)   
 [conj conjf conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)   
 [cimag cimagf cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)   
 [封包，cabsf cabsl](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)