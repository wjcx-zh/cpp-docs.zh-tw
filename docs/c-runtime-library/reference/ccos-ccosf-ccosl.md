---
title: "ccos ccosf ccosl | Microsoft Docs"
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
  - "ccos"
  - "ccosf"
  - "ccosl"
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
  - "ccos"
  - "ccosf"
  - "ccosl"
  - "complex/ccos"
  - "complex/ccosf"
  - "complex/ccosl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "ccos 函式"
  - "ccosf 函式"
  - "ccosl 函式"
ms.assetid: 4ab936ac-ff85-49ac-9418-2b69cf5d4696
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ccos ccosf ccosl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取複數的餘弦函數。  
  
## 語法  
  
```  
_Dcomplex ccos(   
   _Dcomplex z   
);  
_Fcomplex ccos(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex ccos(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex ccosf(   
   _Fcomplex z   
);  
_Lcomplex ccosl(   
   _Lcomplex z   
);  
```  
  
#### 參數  
 `z`  
 表示的角度，以弧度為單位的複數。  
  
## 傳回值  
 餘弦函數 `z`, ，以弧度為單位。  
  
## 備註  
 因為 C\+\+ 允許多載，所以您可以呼叫採用並傳回 `ccos` 和 `_Fcomplex` 值的 `_Lcomplex` 的多載。 在 C 程式中， `ccos` 一律採用並傳回 `_Dcomplex` 值。  
  
## 需求  
  
|常式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`ccos`, `ccosf`, `ccosl`|\<complex.h\>|\< x \>|  
  
 如需相容性詳細資訊，請參閱簡介中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [catanh catanhf catanhl](../../c-runtime-library/reference/catanh-catanhf-catanhl.md)   
 [ctanh ctanhf ctanhl](../../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)   
 [catan catanf catanl](../../c-runtime-library/reference/catan-catanf-catanl.md)   
 [csinh csinhf csinhl](../../c-runtime-library/reference/csinh-csinhf-csinhl.md)   
 [casinh casinhf casinhl](../../c-runtime-library/reference/casinh-casinhf-casinhl.md)   
 [ccosh ccoshf ccoshl](../../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)   
 [cacosh cacoshf cacoshl](../../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)   
 [cacos cacosf cacosl](../../c-runtime-library/reference/cacos-cacosf-cacosl.md)   
 [ctan ctanf ctanl](../../c-runtime-library/reference/ctan-ctanf-ctanl.md)   
 [csin csinf csinl](../../c-runtime-library/reference/csin-csinf-csinl.md)   
 [casin casinf casinl](../../c-runtime-library/reference/casin-casinf-casinl.md)   
 [csqrt csqrtf csqrtl](../../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)