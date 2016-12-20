---
title: "fabs、 fabsf fabsl | Microsoft Docs"
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
  - "fabsf"
  - "fabs"
  - "fabsl"
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
  - "fabs"
  - "fabsf"
  - "fabsl"
  - "math\fabs"
  - "math\fabsf"
  - "math\fabsl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "絕對值"
  - "fabsf 函式"
  - "計算絕對值"
  - "fabs 函式"
  - "fabsl 函式"
ms.assetid: 23bca210-f408-4f5e-b46b-0ccaaec31e36
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fabs、 fabsf fabsl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算浮點引數的絕對值。  
  
## 語法  
  
```  
double fabs(   
   double x   
);  
float fabs(  
   float x   
); // C++ only  
long double fabs(  
   long double x  
); // C++ only  
float fabsf(   
   float x   
);  
long double fabsl(  
   long double x  
);  
```  
  
#### 參數  
 `x`  
 浮點值。  
  
## 傳回值  
 `fabs` 函式會傳回引數的絕對值 `x`。 不會傳回錯誤。  
  
|輸入|SEH 例外狀況|Matherr 例外狀況|  
|--------|--------------|------------------|  
|± QNAN、IND|無|\_DOMAIN|  
  
## 備註  
 C \+ \+ 允許多載，因此您可以呼叫的多載 `fabs` 如果您要加入 \< h \> 標頭。 在 C 程式中， `fabs` 一律採用並傳回雙精度浮點數。  
  
## 需求  
  
|函式|必要的 C 標頭|必要的 c \+ \+ 標頭|  
|--------|--------------|--------------------|  
|`fabs`, `fabsf`, `fabsl`|\<math.h\>|\< h \> 或 \< h.h \>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱範例 [abs](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [abs、 實驗室、 llabs、 \_abs64](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)   
 [\_cabs](../../c-runtime-library/reference/cabs.md)   
 [labs、llabs](../../misc/labs-llabs.md)