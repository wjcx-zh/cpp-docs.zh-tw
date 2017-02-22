---
title: "isnan _isnan _isnanf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_isnan"
  - "_isnanf"
  - "isnan"
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
  - "_isnan"
  - "isnan"
  - "math/isnan"
  - "math/_isnan"
  - "math/_isnanf"
  - "_isnanf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NAN (非數字)"
  - "_isnan 函式"
  - "IEEE 浮點表示"
  - "非數字 (NAN)"
  - "isnan 函式"
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# isnan _isnan _isnanf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

測試的浮點值不是數字 \(NAN\)。  
  
## 語法  
  
```  
int isnan(  
   /* floating-point */ x   
); /* C-only macro */  
  
int _isnan(  
   double x   
);  
  
int _isnanf(  
   float x  
); /* x64 only */  
  
template <class T>  
bool isnan(  
   T x  
) throw(); /* C++ only */  
```  
  
#### 參數  
 *x*  
 要測試的浮點值。  
  
## 傳回值  
 在 C 中， `isnan` 巨集和 `_isnan` 和 `_isnanf` 函式會傳回非零值，如果引數 `x` 為 NAN; 否則傳回 0。  
  
 C \+ \+ `isnan` 範本函式會傳回 `true` 如果引數 `x` 為 NAN，則傳回 `false`。  
  
## 備註  
 C `isnan` 巨集和 `_isnan` 和 `_isnanf` 函式測試的浮點值 *x*, ，傳回非零值，如果 *x* 不是數字 \(NAN\) 值。 浮點運算的結果無法以指定之類型的 IEEE 754 浮點數格式表示，就會產生 NAN。 如需 NAN 如何表示輸出資訊，請參閱 [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)。  
  
 當編譯為 c \+ \+， `isnan` 未定義巨集，以及 `isnan` 改為定義樣板函式。 它會傳回型別的值 `bool` 而不是整數。  
  
 `_isnan` 和 `_isnanf` 函式是 Microsoft 專有的。`_isnanf` 函式只適用於 x64 編譯時。  
  
## 需求  
  
|常式|必要的標頭 \(C\)|必要的標頭 \(C\+\+\)|  
|--------|-----------------|---------------------|  
|`isnan`, `_isnanf`|\<math.h\>|\<math.h\> 或 \<cmath\>|  
|`_isnan`|\<float.h\>|\<.h \> 或 \< cfloat \>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [\_finite、\_finitef](../../c-runtime-library/reference/finite-finitef.md)   
 [\_fpclass \_fpclassf](../../c-runtime-library/reference/fpclass-fpclassf.md)