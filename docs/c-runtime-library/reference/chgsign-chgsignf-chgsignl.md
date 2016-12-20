---
title: "_chgsign、_chgsignf、_chgsignl | Microsoft Docs"
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
  - "_chgsignl"
  - "_chgsign"
  - "_chgsignf"
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
  - "_chgsignf"
  - "chgsign"
  - "_chgsignl"
  - "_chgsign"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_chgsign 函式"
  - "_chgsignf 函式"
  - "_chgsignl 函式"
  - "chgsign 函式"
ms.assetid: a6646f8e-213d-4564-8617-f43bc66f989f
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _chgsign、_chgsignf、_chgsignl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

反轉浮點引數的標記。  
  
## 語法  
  
```  
double _chgsign(   
   double x   
);  
float _chgsignf(  
   float x   
);  
long double _chgsignl(   
   long double x   
);  
```  
  
#### 參數  
 `x`  
 將變更的浮點值。  
  
## 傳回值  
 `_chgsign` 函式會傳回與其原本正副號相反具有浮點引數的 `x`值。  不會回傳錯誤。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_chgsign`|\<float.h\>|  
|`_chgsignf`, `_chgsignl`|\<math.h\>|  
  
 如需詳細的相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [fabs、 fabsf fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [copysign、copysignf、copysignl、\_copysign、\_copysignf、\_copysignl](../../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)