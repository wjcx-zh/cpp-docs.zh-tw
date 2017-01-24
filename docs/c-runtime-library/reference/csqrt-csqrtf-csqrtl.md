---
title: "csqrt csqrtf csqrtl | Microsoft Docs"
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
  - "csqrt"
  - "csqrtf"
  - "csqrtl"
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
  - "csqrt"
  - "csqrtf"
  - "csqrtl"
  - "complex/csqrt"
  - "complex/csqrtf"
  - "complex/csqrtl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "csqrt 函式"
  - "csqrtf 函式"
  - "csqrtl 函式"
ms.assetid: b65f086b-0f55-4622-a7a3-4e79d9c9c05c
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# csqrt csqrtf csqrtl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

與分支沿著負真實軸擷取複雜數字的平方根。  
  
## 語法  
  
```  
_Dcomplex csqrt(   
   _Dcomplex z   
);  
_Fcomplex csqrt(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex csqrt(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex csqrtf(   
   _Fcomplex z   
);  
_Lcomplex csqrtl(   
   _Lcomplex z   
);  
```  
  
#### 參數  
 `z`  
 複數。  
  
## 傳回值  
 平方根 `z`。 結果是以正確的半平面。  
  
|輸入|SEH 例外狀況|`_matherr` 例外狀況|  
|--------|--------------|---------------------|  
|± QNAN、 IND|無|\_DOMAIN|  
|\- ∞|無|\_DOMAIN|  
  
## 備註  
 因為 C\+\+ 允許多載，所以您可以呼叫採用並傳回 `csqrt` 和 `_Fcomplex` 值的 `_Lcomplex` 的多載。 在 C 程式中， `csqrt` 一律採用並傳回 `_Dcomplex` 值。  
  
## 需求  
  
|常式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`csqrt`, `csqrtf`, `csqrtl`|\<complex.h\>|\< x \>|  
  
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
 [ccos ccosf ccosl](../../c-runtime-library/reference/ccos-ccosf-ccosl.md)