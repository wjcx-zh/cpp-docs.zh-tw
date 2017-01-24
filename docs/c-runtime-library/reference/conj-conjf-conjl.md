---
title: "conj conjf conjl | Microsoft Docs"
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
  - "conj"
  - "conjf"
  - "conjl"
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
  - "conj"
  - "conjf"
  - "conjl"
  - "complex/conj"
  - "complex/conjf"
  - "complex/conjl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "conj 函式"
  - "conjf 函式"
  - "conjl 函式"
ms.assetid: 792fccfa-19c6-4890-99f9-a3b89effccd6
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# conj conjf conjl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取複數的共軛複數。  
  
## 語法  
  
```  
_Dcomplex conj(   
   _Dcomplex z   
);  
_Fcomplex conj(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex conj(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex conjf(   
   _Fcomplex z   
);  
_Lcomplex conjl(   
   _Lcomplex z   
);  
```  
  
#### 參數  
 `z`  
 複數。  
  
## 傳回值  
 複雜共軛 `z`。  結果將會有相同的實數和虛數部分為 `z`, ，但正負號相反。  
  
## 備註  
 因為 C\+\+ 允許多載，所以您可以呼叫採用並傳回 `conj` 和 `_Fcomplex` 值的 `_Lcomplex` 的多載。 在 C 程式中， `conj` 一律採用並傳回 `_Dcomplex` 值。  
  
## 需求  
  
|常式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`conj`, `conjf`, `conjl`|\<complex.h\>|\< x \>|  
  
 如需相容性詳細資訊，請參閱簡介中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [norm、 normf norml](../../c-runtime-library/reference/norm-normf-norml1.md)   
 [creal crealf creall](../../c-runtime-library/reference/creal-crealf-creall.md)   
 [cproj cprojf cprojl](../../c-runtime-library/reference/cproj-cprojf-cprojl.md)   
 [cimag cimagf cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)   
 [carg cargf cargl](../../c-runtime-library/reference/carg-cargf-cargl.md)   
 [封包，cabsf cabsl](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)