---
title: "log、logf、log10、log10f | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "log10f"
  - "logf"
  - "log10"
  - "log"
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
  - "logf"
  - "_log10l"
  - "log"
  - "_logl"
  - "log10f"
  - "log10"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "計算對數"
  - "log10f 函式"
  - "log10 函式"
  - "log 函式"
  - "logf 函式"
  - "對數"
ms.assetid: 7adc77c2-04f7-4245-a980-21215563cfae
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# log、logf、log10、log10f
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算。  
  
## 語法  
  
```  
  
      double log(  
   double x   
);  
float log(  
   float x  
);  // C++ only  
long double log(  
   long double x  
);  // C++ only  
float logf(  
   float x   
);  
double log10(  
   double x  
);  
float log10(  
   float x  
);  // C++ only  
long double log10(  
   long double x  
);  // C++ only  
float log10f (  
   float x  
);  
```  
  
#### 參數  
 *x*  
 要找出其對數的值。  
  
## 傳回值  
 **log** 函式傳回自然對數 \(基底 *x* e\)，如果成功。  log10 函式傳回以 10 為基底之對數。  如果 *x* 為負數，這些函式會傳回不確定，預設為。  如果 *x* 為 0，則會傳回 INF \(無限\)。  
  
|輸入|SEH 例外狀況|Matherr 例外狀況|  
|--------|--------------|------------------|  
|± QNAN,IND|無|\_DOMAIN|  
|± 0|ZERODIVIDE|\_SING|  
|x \< 0|INVALID|\_DOMAIN|  
  
 **log** 與 `log10` 會使用 Streaming SIMD Extensions 2\(SSE2\) 的實作。  請參閱 [\_set\_SSE2\_enable](../../c-runtime-library/reference/set-sse2-enable.md) 以取得詳細資訊及使用限制 SSE2 實作。  
  
## 備註  
 C\+\+ 允許多載，因此您可以呼叫 **log**和 `log10` 的多載。  在 C 程式，**log** 和 `log10` 一律接受並傳回 。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|**log**, `logf`, `log10`, `log10f`|\<math.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_log.c  
/* This program uses log and log10  
 * to calculate the natural logarithm and  
 * the base-10 logarithm of 9,000.  
 */  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 9000.0;  
   double y;  
  
   y = log( x );  
   printf( "log( %.2f ) = %f\n", x, y );  
   y = log10( x );  
   printf( "log10( %.2f ) = %f\n", x, y );  
}  
```  
  
## Output  
  
```  
log( 9000.00 ) = 9.104980  
log10( 9000.00 ) = 3.954243  
```  
  
 若要產生其他基底對數，請使用數學關聯性 \(式\):記錄 \=\= 自然對數 \(a\)\/自然對數 \(B\) 的基礎 b。  
  
```  
// logbase.cpp  
#include <math.h>  
#include <stdio.h>  
  
double logbase(double a, double base)  
{  
   return log(a) / log(base);  
}  
  
int main()  
{  
   double x = 65536;  
   double result;  
  
   result = logbase(x, 2);  
   printf("Log base 2 of %lf is %lf\n", x, result);  
}  
```  
  
## Output  
  
```  
Log base 2 of 65536.000000 is 16.000000  
```  
  
## .NET Framework 對等用法  
  
-   [System::Math::Log](https://msdn.microsoft.com/en-us/library/system.math.log.aspx)  
  
-   [System::Math::Log10](https://msdn.microsoft.com/en-us/library/system.math.log10.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [exp、expf](../../c-runtime-library/reference/exp-expf.md)   
 [\_matherr](../../c-runtime-library/reference/matherr.md)   
 [pow、powf、powl](../../c-runtime-library/reference/pow-powf-powl.md)   
 [\_CIlog](../../c-runtime-library/cilog.md)   
 [\_CIlog10](../../c-runtime-library/cilog10.md)