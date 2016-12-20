---
title: "fpclassify | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fpclassify"
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
apitype: "HeaderDef"
f1_keywords: 
  - "fpclassify"
  - "math/fpclassify"
helpviewer_keywords: 
  - "fpclassify 巨集"
  - "fpclassify 函式"
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fpclassify
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回引數的浮點數的分類。  
  
## 語法  
  
```  
int fpclassify(   
   /* floating-point */ x   
);  
  
int fpclassify(   
   float x   
); // C++ only  
  
int fpclassify(   
   double x   
); // C++ only  
  
int fpclassify(   
   long double x   
); // C++ only  
  
```  
  
#### 參數  
 `x`  
 要測試的浮點值。  
  
## 傳回值  
 `fpclassify` 傳回整數值，指出引數的浮點數類別 `x`。 下表顯示可能的值傳回 `fpclassify`, ，定義在 \< h.h \>。  
  
|值|描述|  
|-------|--------|  
|`FP_NAN`|無訊息、 信號，或不確定的 NaN|  
|`FP_INFINITE`|無限大的正數或負數|  
|`FP_NORMAL`|正數或負數正規化非零值|  
|`FP_SUBNORMAL`|正數或負數反正規化的值|  
|`FP_ZERO`|正或負零值|  
  
## 備註  
 在 C 中， `fpclassify` 是巨集，在 c \+ \+， `fpclassify` 是函式多載使用引數型別 `float`, ，`double`, ，或 `long double`。 在任一情況下，傳回的值取決於有效運算式的型別引數，以及不在任何中繼的表示法。 例如，一般 `double` 或 `long double` 值會是無限值、 異常，或零值轉換為 `float`。  
  
## 需求  
  
|函式\/巨集|必要的標頭 \(C\)|必要的標頭 \(C\+\+\)|  
|------------|-----------------|---------------------|  
|`fpclassify`|\<math.h\>|\<math.h\> 或 \<cmath\>|  
  
 `fpclassify` 巨集和 `fpclassify` 函式符合 C99 和 C \+ \+ 11 規格。 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [isnan \_isnan \_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)