---
title: "expm1、expm1f、expm1l | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "expm1l"
  - "expm1"
  - "expm1f"
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
  - "expm1l"
  - "expm1"
  - "expm1f"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "expm1 函式"
  - "expm1f 函式"
  - "expm1l 函式"
ms.assetid: 2a4dd2d9-370c-42b0-9067-0625efa272e0
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# expm1、expm1f、expm1l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算值的基底 e 指數，減一。  
  
## 語法  
  
```  
double expm1(   
   double x   
);  
float expm1(  
   float x  
);  // C++ only  
long double expm1(  
   long double x  
);  // C++ only  
float expm1f(  
   float x  
);  
long double expm1l(  
   long double x  
);  
```  
  
#### 參數  
 `x`  
 浮點指數值。  
  
## 傳回值  
 如果成功，`expm1` 函式會傳回代表 e<sup>x</sup> – 1 的浮點值。  溢位時，`expm1` 傳回 `HUGE_VAL`；`expm1f` 傳回 `HUGE_VALF`；`expm1l` 傳回 `HUGE_VALL`，而且 `errno` 設為 `ERANGE`。  如需傳回碼的詳細資訊，請參閱[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 因為 C\+\+ 允許多載，您可以呼叫會接受並傳回 `float` 和 `long double` 值的 `expm1` 多載。  在 C 程式，`expm1` 一律接受並傳回 `double`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`expm1`, `expm1f`, `expm1l`|\<math.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [exp2、exp2f、exp2l](http://msdn.microsoft.com/zh-tw/a7974629-be1e-4196-a562-6624a0732003)   
 [pow、powf、powl](../../c-runtime-library/reference/pow-powf-powl.md)