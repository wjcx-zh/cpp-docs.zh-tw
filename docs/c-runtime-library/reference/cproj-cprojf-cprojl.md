---
title: "cproj cprojf cprojl | Microsoft Docs"
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
  - "cproj"
  - "cprojf"
  - "cprojl"
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
  - "cproj"
  - "cprojf"
  - "cprojl"
  - "complex/cproj"
  - "complex/cprojf"
  - "complex/cprojl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "cproj 函式"
  - "cprojf 函式"
  - "cprojl 函式"
ms.assetid: 32b49623-13bf-4cae-802e-7912d75030fe
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# cproj cprojf cprojl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取複數 Reimann 球面上的投影。  
  
## 語法  
  
```  
_Dcomplex cproj(   
   _Dcomplex z   
);  
_Fcomplex cproj(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex cproj(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex cprojf(   
   _Fcomplex z   
);  
_Lcomplex cprojl(   
   _Lcomplex z   
);  
```  
  
#### 參數  
 `z`  
 複數。  
  
## 傳回值  
 投影 `z` Reimann 球體。  
  
## 備註  
 因為 C\+\+ 允許多載，所以您可以呼叫採用並傳回 `cproj` 和 `_Fcomplex` 值的 `_Lcomplex` 的多載。 在 C 程式中， `cproj` 一律採用並傳回 `_Dcomplex` 值。  
  
## 需求  
  
|常式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`cproj`, `cprojf`, `cprojl`|\<complex.h\>|\< x \>|  
  
 如需相容性詳細資訊，請參閱簡介中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [norm、 normf norml](../../c-runtime-library/reference/norm-normf-norml1.md)   
 [creal crealf creall](../../c-runtime-library/reference/creal-crealf-creall.md)   
 [conj conjf conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)   
 [cimag cimagf cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)   
 [carg cargf cargl](../../c-runtime-library/reference/carg-cargf-cargl.md)   
 [封包，cabsf cabsl](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)