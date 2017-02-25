---
title: "floor、floorf、floorl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "floorf"
  - "floorl"
  - "floor"
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
  - "floor"
  - "floorl"
  - "_floorl"
  - "floorf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "計算值的下限"
  - "floor 函式"
  - "floorf 函式"
  - "floorl 函式"
ms.assetid: e9955f70-d659-414f-8050-132e13c8ff36
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# floor、floorf、floorl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算值的最低限度值。  
  
## 語法  
  
```  
double floor(  
   double x  
);  
float floor(  
   float x   
); // C++ only  
long double floor(  
   long double x  
); // C++ only  
float floorf(  
   float x  
);  
long double floorl(  
   long double x  
);  
```  
  
#### 參數  
 `x`  
 浮點值  
  
## 傳回值  
 `floor` 函式會傳回表示小於或等於 `x`的最大的整數值的浮點值。  不會回傳錯誤。  
  
|輸入|SEH 例外狀況|Matherr 例外狀況|  
|--------|--------------|------------------|  
|± QNAN,IND|無|\_DOMAIN|  
  
 `floor` 會使用 Streaming SIMD Extensions 2\(SSE2\) 的實作。  如需有關使用 SSE2 實作的詳細資訊和限制，請參閱 [\_set\_SSE2\_enable](../../c-runtime-library/reference/set-sse2-enable.md)。  
  
## 備註  
 C\+\+ 允許多載，因此您可以呼叫會接受並傳回 `float` 與 `long double` 值的 `floor` 多載。  在 C 程式，`floor` 一律接受並傳回 `double`。  
  
## 需求  
  
|Function|必要的標頭|  
|--------------|-----------|  
|`floor`, `floorf`, `floorl`|\<math.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_floor.c  
// This example displays the largest integers  
// less than or equal to the floating-point values 2.8  
// and -2.8. It then shows the smallest integers greater  
// than or equal to 2.8 and -2.8.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double y;  
  
   y = floor( 2.8 );  
   printf( "The floor of 2.8 is %f\n", y );  
   y = floor( -2.8 );  
   printf( "The floor of -2.8 is %f\n", y );  
  
   y = ceil( 2.8 );  
   printf( "The ceil of 2.8 is %f\n", y );  
   y = ceil( -2.8 );  
   printf( "The ceil of -2.8 is %f\n", y );  
}  
```  
  
  **2.8 的最低限度值為 2.000000。**  
**\-2.8 的最低限度值為 \-3.000000。**  
**2.8 的 ceil 是 3.000000**  
**\-2.8 的 ceil 是 \-2.000000**   
## .NET Framework 對等用法  
 [System::Math::Floor](https://msdn.microsoft.com/en-us/library/system.math.floor.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [ceil、ceilf、ceill](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [round、roundf、roundl](../../c-runtime-library/reference/round-roundf-roundl.md)   
 [fmod、fmodf](../../c-runtime-library/reference/fmod-fmodf.md)