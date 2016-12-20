---
title: "cacosh cacoshf cacoshl | Microsoft Docs"
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
  - "cacosh"
  - "cacoshf"
  - "cacoshl"
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
  - "cacosh"
  - "cacoshf"
  - "cacoshl"
  - "complex/cacosh"
  - "complex/cacoshf"
  - "complex/cacoshl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "cacosh 函式"
  - "cacoshf 函式"
  - "cacoshl 函式"
ms.assetid: 83fd05eb-3587-4741-9be6-589a830a1703
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# cacosh cacoshf cacoshl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取複數的反雙曲餘弦值小於 1 真實軸剪下分支。 .  
  
## 語法  
  
```  
_Dcomplex cacosh(   
   _Dcomplex z   
);  
_Fcomplex cacosh(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex cacosh(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex cacoshf(   
   _Fcomplex z   
);  
_Lcomplex cacoshl(   
   _Lcomplex z   
);  
```  
  
#### 參數  
 `z`  
 代表角度，以弧度為單位的複數。  
  
## 傳回值  
 反雙曲餘 `z`, ，以弧度為單位。 結果是未繫結和非負真實座標軸和虛數軸間隔 \[−iπ，\+ iπ\] 中。  
  
## 備註  
 因為 C\+\+ 允許多載，所以您可以呼叫採用並傳回 `cacosh` 和 `_Fcomplex` 值的 `_Lcomplex` 的多載。 在 C 程式中， `cacosh` 一律採用並傳回 `_Dcomplex` 值。  
  
## 需求  
  
|常式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`cacosh`, `cacoshf`, `cacoshl`|\<complex.h\>|\< x \>|  
  
 如需相容性詳細資訊，請參閱簡介中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [catanh catanhf catanhl](../../c-runtime-library/reference/catanh-catanhf-catanhl.md)   
 [ctanh ctanhf ctanhl](../../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)   
 [catan catanf catanl](../../c-runtime-library/reference/catan-catanf-catanl.md)   
 [csinh csinhf csinhl](../../c-runtime-library/reference/csinh-csinhf-csinhl.md)   
 [casinh casinhf casinhl](../../c-runtime-library/reference/casinh-casinhf-casinhl.md)   
 [ccosh ccoshf ccoshl](../../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)   
 [cacos cacosf cacosl](../../c-runtime-library/reference/cacos-cacosf-cacosl.md)   
 [ctan ctanf ctanl](../../c-runtime-library/reference/ctan-ctanf-ctanl.md)   
 [csin csinf csinl](../../c-runtime-library/reference/csin-csinf-csinl.md)   
 [casin casinf casinl](../../c-runtime-library/reference/casin-casinf-casinl.md)   
 [ccos ccosf ccosl](../../c-runtime-library/reference/ccos-ccosf-ccosl.md)   
 [csqrt csqrtf csqrtl](../../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)