---
title: "logb、logbf、logbl、_logb、_logbf | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "logb"
  - "_logb"
  - "_logbl"
  - "logbf"
  - "logbl"
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
  - "logb"
  - "logbl"
  - "_logb"
  - "_logbf"
  - "logbf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_logb 函式"
  - "_logbf 函式"
  - "指數, 浮點數"
  - "指數和尾數"
  - "浮點函式"
  - "浮點函式, 尾數和指數"
  - "logb 函式"
  - "logbf 函式"
  - "logbl 函式"
  - "尾數, 浮點變數"
ms.assetid: 780c4daa-6fe6-4fbc-9412-4c1ba1a1766f
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# logb、logbf、logbl、_logb、_logbf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取浮點引數的指數值。  
  
## 語法  
  
```  
double logb(  
   double x   
);  
float logb(  
   float x   
); // C++ only  
long double logb(  
   long double x   
); // C++ only   
float logbf(  
   float x   
);  
long double logbl(  
   long double x   
);  
double _logb(  
   double x   
);  
float _logbf(  
   float x   
);  
```  
  
#### 參數  
 x  
 浮點值。  
  
## 傳回值  
 `logb` 傳回 `x` 的無偏差指數值，帶正負號的整數表示為浮點值。  
  
## 備註  
 `logb` 函式擷取浮點引數 `x` 的指數值，假定 `x` 使用無限範圍表示。  如果 `x` 被非標準化，則會將它視為標準化。  
  
 因為 C\+\+ 允許多載，您可以呼叫會接受並傳回 `float` 或 `long double` 值的 `logb` 多載。  在 C 程式，`logb` 一律接受並傳回 `double`。  
  
|輸入|SEH 例外狀況|Matherr 例外狀況|  
|--------|--------------|------------------|  
|± QNAN,IND|None|\_DOMAIN|  
|± 0|ZERODIVIDE|\_SING|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_logb`|\<float.h\>|  
|`logb`, `logbf`, `logbl`, `_logbf`|\<math.h\>|  
  
 如需詳細的相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)