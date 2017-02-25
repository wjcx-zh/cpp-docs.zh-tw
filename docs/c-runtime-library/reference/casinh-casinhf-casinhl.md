---
title: "casinh casinhf casinhl | Microsoft Docs"
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
  - "casinh"
  - "casinhl"
  - "casinhf"
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
  - "casinh"
  - "casinhf"
  - "casinhl"
  - "complex/casinh"
  - "complex/casinhf"
  - "complex/casinhl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "casinh 函式"
  - "casinhf 函式"
  - "casinhl 函式"
ms.assetid: bd18340b-21dd-4c86-a14e-e8e15dd97e3b
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# casinh casinhf casinhl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取間隔之外的分支剪下與複數的反雙曲線正弦 \[−i，\+ 我\] 虛數軸。  
  
## 語法  
  
```  
_Dcomplex casinh(   
   _Dcomplex z   
);  
_Fcomplex casinh(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex casinh(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex casinhf(   
   _Fcomplex z   
);  
_Lcomplex casinhl(   
   _Lcomplex z   
);  
```  
  
#### 參數  
 `z`  
 代表角度，以弧度為單位的複數。  
  
## 傳回值  
 反雙曲線正弦 `z`, ，以弧度為單位。 結果是真實座標軸和虛數軸間隔 \[−iπ\/2 \+ iπ\/2\] 中，未繫結。  
  
## 備註  
 因為 C\+\+ 允許多載，所以您可以呼叫採用並傳回 `casinh` 和 `_Fcomplex` 值的 `_Lcomplex` 的多載。 在 C 程式中， `casinh` 一律採用並傳回 `_Dcomplex` 值。  
  
## 需求  
  
|常式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`casinh`, `casinhf`, `casinhl`|\<complex.h\>|\< x \>|  
  
 如需相容性詳細資訊，請參閱簡介中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [catanh catanhf catanhl](../../c-runtime-library/reference/catanh-catanhf-catanhl.md)   
 [ctanh ctanhf ctanhl](../../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)   
 [catan catanf catanl](../../c-runtime-library/reference/catan-catanf-catanl.md)   
 [csinh csinhf csinhl](../../c-runtime-library/reference/csinh-csinhf-csinhl.md)   
 [ccosh ccoshf ccoshl](../../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)   
 [cacosh cacoshf cacoshl](../../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)   
 [cacos cacosf cacosl](../../c-runtime-library/reference/cacos-cacosf-cacosl.md)   
 [ctan ctanf ctanl](../../c-runtime-library/reference/ctan-ctanf-ctanl.md)   
 [csin csinf csinl](../../c-runtime-library/reference/csin-csinf-csinl.md)   
 [casin casinf casinl](../../c-runtime-library/reference/casin-casinf-casinl.md)   
 [ccos ccosf ccosl](../../c-runtime-library/reference/ccos-ccosf-ccosl.md)   
 [csqrt csqrtf csqrtl](../../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)