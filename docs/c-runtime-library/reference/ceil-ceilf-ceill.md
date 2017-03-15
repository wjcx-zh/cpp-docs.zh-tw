---
title: "ceil、ceilf、ceill | Microsoft Docs"
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
  - "ceilf"
  - "ceil"
  - "ceill"
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
  - "ceil"
  - "ceilf"
  - "ceill"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "計算值上限"
  - "ceil 函式"
  - "ceilf 函式"
  - "ceill 函式"
ms.assetid: f4e5acab-5c8f-4b10-9ae2-9561e6453718
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ceil、ceilf、ceill
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算值的最高限度值。  
  
## 語法  
  
```  
double ceil(   
   double x   
);  
float ceil(  
   float x  
);  // C++ only  
long double ceil(  
   long double x  
);  // C++ only  
float ceilf(  
   float x  
);  
long double ceill(  
   long double x  
);  
```  
  
#### 參數  
 `x`  
 浮點值  
  
## 傳回值  
 `ceil` 函式會傳回表示大於或等於 `x`的最小的整數值的浮點值。  不會回傳錯誤。  
  
|輸入|SEH 例外狀況|Matherr 例外狀況|  
|--------|--------------|------------------|  
|± `QNAN`,`IND`|無|`_DOMAIN`|  
  
 `ceil` 會使用 Streaming SIMD Extensions 2\(SSE2\) 的實作。  如需有關使用 SSE2 實作的詳細資訊和限制，請參閱 [\_set\_SSE2\_enable](../../c-runtime-library/reference/set-sse2-enable.md)。  
  
## 備註  
 因為 C\+\+ 允許多載，您可以呼叫 `ceil` 的多載。  在 C 程式裏 `ceil` 一律接受並傳回雙精度浮點數。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`ceil`, `ceilf`, `ceill`|\<math.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [floor](../../c-runtime-library/reference/floor-floorf-floorl.md) 的範例。  
  
## .NET Framework 對等用法  
 [System::Math::Ceiling](https://msdn.microsoft.com/en-us/library/system.math.ceiling.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [floor、floorf、floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [fmod、fmodf](../../c-runtime-library/reference/fmod-fmodf.md)   
 [round、roundf、roundl](../../c-runtime-library/reference/round-roundf-roundl.md)