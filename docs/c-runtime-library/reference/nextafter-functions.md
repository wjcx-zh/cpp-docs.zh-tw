---
title: "nextafter、 nextafterf、 nextafterl、 _nextafter、 _nextafterf、 nexttoward、 nexttowardf、 nexttowardl | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "nextafterf"
  - "_nextafterf"
  - "nextafter"
  - "nextafterl"
  - "_nextafter"
  - "nexttoward"
  - "nexttowardf"
  - "nexttowardl"
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
  - "nextafter"
  - "_nextafter"
  - "nextafterf"
  - "nextafterl"
  - "_nextafterf"
  - "math/nextafter"
  - "math/nextafterf"
  - "math/nextafterl"
  - "nexttoward"
  - "nexttowardf"
  - "nexttowardl"
  - "math/nexttoward"
  - "math/nexttowardf"
  - "math/nexttowardl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_nextafter 函式"
  - "nextafter 函式"
  - "_nextafterf 函式"
  - "nextafterf 函式"
  - "nextafterl 函式"
  - "nexttoward 函式"
  - "nexttowardf 函式"
  - "nexttowardl 函式"
ms.assetid: 9785bfb9-de53-4bd0-9637-f05fa0c1f6ab
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# nextafter、 nextafterf、 nextafterl、 _nextafter、 _nextafterf、 nexttoward、 nexttowardf、 nexttowardl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回下一步表示浮點值。  
  
## 語法  
  
```  
double nextafter(  
   double x,  
   double y   
);  
  
float nextafter(  
   float x,  
   float y   
); /* C++ only, requires <cmath> */  
  
long double nextafter(  
   long double x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
float nextafterf(  
   float x,  
   float y   
);   
  
long double nextafterl(  
   long double x,  
   long double y   
);  
  
double _nextafter(  
   double x,  
   double y   
);  
  
float _nextafterf(  
   float x,  
   float y   
); /* x64 only */  
  
double nexttoward(  
   double x,  
   long double y   
);  
  
float nexttoward(  
   float x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
long double nexttoward(  
   long double x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
float nexttowardf(  
   float x,  
   long double y   
);   
  
long double nexttowardl(  
   long double x,  
   long double y   
);  
```  
  
#### 參數  
 `x`  
 要從啟動的浮點值。  
  
 `y`  
 要移往的浮點值。  
  
## 傳回值  
 傳回下一步表示浮點值之後，傳回類型 `x` 方向 `y`。 如果 `x`\=`y`, ，此函數會傳回 `y`, ，轉換成與觸發任何例外狀況的傳回型別。 如果 `x` 不等於 `y`, ，結果 denormal 或零、 FE\_UNDERFLOW 和 FE\_INEXACT 的浮點例外狀況狀態已設定，且會傳回正確的結果。 如果 `x` 或 `y` 為 NAN，則傳回值是 「 一輸入 Nan。 如果 `x` 是有限的結果是無限或型別中無法顯示，傳回正確簽署的 infinity 或 NAN，FE\_OVERFLOW 和 FE\_INEXACT 的浮點例外狀況狀態已設定，以及 `errno` 設為 ERANGE。  
  
## 備註  
 `nextafter` 和 `nexttoward` 系列函式是相等的除了的參數型別 `y`。 如果 `x` 和 `y` 相等，傳回的值為 `y` 轉換為傳回型別。  
  
 因為 c \+ \+ 允許多載，如果您要加入 \< h \>，所以您可以呼叫的多載 `nextafter` 和 `nexttoward` ，會傳回 `float` 和 `long double` 型別。 在 C 程式中， `nextafter` 和 `nexttoward` 一律會傳回 `double`。  
  
 `_nextafter` 和 `_nextafterf` 函式是 Microsoft 專有的。`_nextafterf` 對於 x64 編譯時，才可使用函式。  
  
## 需求  
  
|常式|必要的標頭 \(C\)|必要的標頭 \(C\+\+\)|  
|--------|-----------------|---------------------|  
|`nextafter`, `nextafterf`, `nextafterl`, `_nextafterf`, `nexttoward`, `nexttowardf`, `nexttowardl`|\<math.h\>|\<math.h\> 或 \<cmath\>|  
|`_nextafter`|\<float.h\>|\<.h \> 或 \< cfloat \>|  
  
 如需相容性詳細資訊，請參閱簡介中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [isnan \_isnan \_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)