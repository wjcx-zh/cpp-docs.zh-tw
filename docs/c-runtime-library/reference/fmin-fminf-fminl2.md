---
title: "fmin、 fminf、 fminl | Microsoft Docs"
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
  - "fmin"
  - "fminf"
  - "fminl"
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
  - "fmin"
  - "fminf"
  - "fminl"
  - "math/fmin"
  - "math/fminf"
  - "math/fminl"
helpviewer_keywords: 
  - "fmin 函式"
  - "fminf 函式"
  - "fminl 函式"
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fmin、 fminf、 fminl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

決定使用較小的兩個指定的值。  
  
## 語法  
  
```  
double fmin(  
   double x,   
   double y  
);  
  
float fmin(  
   float x,   
   float y  
); //C++ only  
  
long double fmin(  
   long double x,   
   long double y  
); //C++ only  
  
float fminf(  
   float x,   
   float y  
);  
  
long double fminl(  
   long double x,   
   long double y  
);  
  
```  
  
#### 參數  
 `x`  
 要比較的第一個值。  
  
 `y`  
 要比較的第二個值。  
  
## 傳回值  
 如果成功，傳回較小的 `x` 或 `y`。  
  
|輸入|結果|  
|--------|--------|  
|`x` 是 NaN|`y`|  
|`y` 是 NaN|`x`|  
|`x` 和 `y` 是 NaN|nan|  
  
 函式不會造成 [\_matherr](../../c-runtime-library/reference/matherr.md) 要叫用任何浮點例外狀況，或變更的值 `errno`。  
  
## 備註  
 因為 c \+ \+ 允許多載，所以您可以呼叫的多載 `fmin` 採用並傳回浮點和長雙精度浮點型別。 在 C 程式中， `fmin` 一律採用並傳回雙精度浮點數。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`fmin`, `fminf`,  `fminl`|C: \< h.h \><br /><br /> C \+ \+: \< h.h \> 或 \< h \>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)