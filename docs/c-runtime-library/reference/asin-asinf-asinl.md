---
title: "asin、asinf、asinl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "asinf"
  - "asinl"
  - "asin"
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
  - "asin"
  - "asinl"
  - "asinf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "arcsine 函式"
  - "asin 函式"
  - "asinf 函式"
  - "asinl 函式"
  - "三角函式"
ms.assetid: ca05f9ea-b711-49f6-9f32-2f4019abfd69
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# asin、asinf、asinl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算反正弦函式。  
  
## 語法  
  
```  
double asin(   
   double x   
);  
float asin(  
   float x  
);  // C++ only  
long double asin(  
   long double x  
);  // C++ only  
float asinf (   
   float x   
);  
long double asinl(  
   long double x  
);  
```  
  
#### 參數  
 `x`  
 反正弦值要計算的值。  
  
## 傳回值  
 `asin` 函式傳回的反正弦值 \(反正弦函數\)範圍的 `x` 對π\/2 弧度的π\/2。  
  
 根據預設，如果 `x` 小於 \-1 或大於 1 ， `asin` 函式的回傳結果是未定義的。  
  
|輸入|SEH 例外狀況|Matherr 例外狀況|  
|--------|--------------|------------------|  
|± ∞|`INVALID`|`_DOMAIN`|  
|± `QNAN`,`IND`|無|`_DOMAIN`|  
|&#124;x&#124;\>1|`INVALID`|`_DOMAIN`|  
  
## 備註  
 因為 C\+\+ 允許多載，您可以呼叫 `asin` 多載與 `float` 和 `long double` 的值。  在 C 程式裏 `asin` 一律接受並傳回雙精度浮點數。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`asin`, `asinf`, `asinl`|\<math.h\>|  
  
## 範例  
 如需詳細資訊，請參閱[acos、acosf、acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)。  
  
## .NET Framework 對等用法  
 [System::Math::Asin](https://msdn.microsoft.com/en-us/library/system.math.asin.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [acos、acosf、acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [atan、atanf、atanl、atan2、atan2f、atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [cos、cosf、cosl、cosh、coshf、coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [\_matherr](../../c-runtime-library/reference/matherr.md)   
 [sin、sinf、sinl、sinh、sinhf、sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan、tanf、tanl、tanh、tanhf、tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)