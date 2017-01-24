---
title: "pow、powf、powl | Microsoft Docs"
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
  - "powl"
  - "pow"
  - "powf"
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
  - "powl"
  - "pow"
  - "_powl"
  - "powf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_powl 函式"
  - "計算指數"
  - "指數計算"
  - "取冪"
  - "pow 函式"
  - "乘冪, 計算"
  - "powf 函式"
  - "powl 函式"
ms.assetid: e75c33ed-2e59-48b1-be40-81da917324f1
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# pow、powf、powl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算 `x` 的 `y` 乘冪數。  
  
## 語法  
  
```  
double pow(  
   double x,  
   double y   
);  
double pow(  
   double x,  
   int y  
);  // C++ only  
float pow(  
   float x,  
   float y   
);  // C++ only  
float pow(  
   float x,  
   int y  
);  // C++ only  
long double pow(  
   long double x,  
   long double y  
);  // C++ only  
long double pow(  
   long double x,  
   int y  
);  // C++ only  
float powf(  
   float x,  
   float y   
);  
long double powl(  
   long double x,  
   long double y  
);  
```  
  
#### 參數  
 `x`  
 基底  
  
 `y`  
 指數。  
  
## 傳回值  
 傳回 `x`<sup>y</sup> 的値。  錯誤訊息在溢位或反向溢位時不會列印。  
  
|x 和 y 的值|傳回值 pow|  
|--------------|-------------|  
|`x` \< \> 0 和 `y` \= 0.0|1|  
|`x` \= 0.0 和 `y` \= 0.0|1|  
|`x` \= 0.0 和 `y` \< 0|INF|  
  
## 備註  
 `pow` 無法辨識整數浮點值大於 2<sup>64</sup> \(例如， `1.0E100`\)。  
  
 `pow` 會使用 Streaming SIMD Extensions 2\(SSE2\) 的實作。  如需有關使用 SSE2 實作的詳細資訊和限制，請參閱 [\_set\_SSE2\_enable](../../c-runtime-library/reference/set-sse2-enable.md)。  
  
 因為 C\+\+ 允許多載，您可以呼叫任何 `pow`的各種多載。  在 C 程式中， `pow` 一律接受並傳回雙精確度浮點數值。  
  
 `pow(int, int)` 多載無法使用。  如果您使用這個多載，編譯器可能會發出 C2668。  若要避免這個問題，請轉換第一個參數為 `double`、 `float`或 `long double`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`pow`, `powf`, `powl`|\<math.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_pow.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.0, y = 3.0, z;  
  
   z = pow( x, y );  
   printf( "%.1f to the power of %.1f is %.1f\n", x, y, z );  
}  
```  
  
## Output  
  
```  
2.0 to the power of 3.0 is 8.0  
```  
  
## .NET Framework 對等用法  
 [System::Math::Pow](https://msdn.microsoft.com/en-us/library/system.math.pow.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [exp、expf](../../c-runtime-library/reference/exp-expf.md)   
 [log、logf、log10、log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)   
 [sqrt、sqrtf、sqrtl](../../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)   
 [\_CIpow](../../c-runtime-library/cipow.md)