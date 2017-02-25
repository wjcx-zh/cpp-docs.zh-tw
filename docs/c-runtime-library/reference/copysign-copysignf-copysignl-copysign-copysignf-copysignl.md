---
title: "copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "copysignf"
  - "copysignl"
  - "_copysignl"
  - "_copysign"
  - "_copysignf"
  - "copysign"
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
  - "_copysignl"
  - "copysign"
  - "copysignf"
  - "_copysign"
  - "copysignl"
  - "_copysignf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_copysign 函式"
  - "_copysignf 函式"
  - "_copysignl 函式"
  - "copysign 函式"
  - "copysignf 函式"
  - "copysignl 函式"
ms.assetid: 009216d6-72a2-402d-aa6c-91d924b2c9e4
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回某值，其具有一個引數之範圍和其他引數的符號。  
  
## 語法  
  
```  
double copysign(   
   double x,  
   double y   
);  
float copysign(   
   float x,  
   float y   
); // C++ only  
long double copysign(   
   long double x,  
   long double y   
); // C++ only  
float copysignf(   
   float x,  
   float y   
); // C++ only  
long double copysignl(   
   long double x,  
   long double y   
); // C++ only  
double _copysign(   
   double x,  
   double y   
);  
long double _copysignl(   
   long double x,  
   long double y   
);  
```  
  
#### 參數  
 `x`  
 浮點數值，其被傳回為此結果範圍。  
  
 `y`  
 浮點數值，其被傳回為此結果的符號。  
  
 [浮點支援常式](../../c-runtime-library/floating-point-support.md)  
  
## 傳回值  
 `copysign` 函式傳回浮點值，其結合 `x`的大小和 `y`的符號。  不會回傳錯誤。  
  
## 備註  
 因為 C\+\+ 允許多載，您可以呼叫會接受並傳回 `float` 或 `long double` 值的 `copysign` 多載。  在 C 程式，`copysign` 一律接受並傳回 `double`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_copysign`|\<float.h\>|  
|`copysign`, `copysignf`, `copysignl`, `_copysignf` `_copysignl`|\<math.h\>|  
  
 如需詳細的相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [fabs、 fabsf fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [\_chgsign、\_chgsignf、\_chgsignl](../../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)