---
title: "exp、expf | Microsoft Docs"
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
  - "expf"
  - "exp"
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
  - "_expl"
  - "expf"
  - "exp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "指數計算"
  - "expf 函式"
  - "計算指數"
  - "exp 函式"
ms.assetid: 7070016d-1143-407e-9e9a-6b059bb88867
caps.latest.revision: 13
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# exp、expf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算指數。  
  
## 語法  
  
```  
double exp(   
   double x  
);  
float exp(  
   float x  
);  // C++ only  
long double exp(  
   long double x  
);  // C++ only  
float expf(   
   float x  
);  
```  
  
#### 參數  
 `x`  
 浮點值  
  
## 傳回值  
 `exp` 函式會傳回浮點參數，如果成功則傳回 `x`的指數值。  即結果為 e 至乘冪 `x`， e 是自然對數的底數。  在溢位，函式會傳回 INF \(無限\) 及反向溢位， `exp` 會傳回 0。  
  
|輸入|SEH 例外狀況|Matherr 例外狀況|  
|--------|--------------|------------------|  
|± QNAN,IND|無|\_DOMAIN|  
|± ∞|INVALID|\_DOMAIN|  
|x ≥ 7.097827e\+002|INEXACT\+OVERFLOW|OVERFLOW|  
|x ≤ \-7.083964e\+002|INEXACT\+UNDERFLOW|反向溢位|  
  
 `exp` 會使用 Streaming SIMD Extensions 2\(SSE2\) 的實作。  請參閱 [\_set\_SSE2\_enable](../../c-runtime-library/reference/set-sse2-enable.md) 以取得詳細資訊及使用限制 SSE2 實作。  
  
## 備註  
 C\+\+ 允許多載，因此您可以呼叫 `exp` 不同版本的多載。  在 C 程式裏 `exp` 一律接受並傳回雙精度浮點數。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`exp`, `expf`|\<math.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_exp.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.302585093, y;  
  
   y = exp( x );  
   printf( "exp( %f ) = %f\n", x, y );  
}  
```  
  
  **exp\( 2.302585 \) \= 10.000000**   
## .NET Framework 對等用法  
 [System::Math::Exp](https://msdn.microsoft.com/en-us/library/system.math.exp.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [log、logf、log10、log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)   
 [\_CIexp](../../c-runtime-library/ciexp.md)