---
title: "_cabs | Microsoft Docs"
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
  - "_cabs"
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
  - "cabsl"
  - "_cabs"
  - "_cabsl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_cabs 函式"
  - "_cabsl 函式"
  - "絕對值"
  - "cabs 函式"
  - "cabsl 函式"
  - "計算絕對值"
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
caps.latest.revision: 13
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _cabs
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算複數的絕對值。  
  
## 語法  
  
```  
double _cabs(   
   struct _complex z   
);  
```  
  
#### 參數  
 `z`  
 複數  
  
## 傳回值  
 如果成功，`_cabs` 傳回它的引數的絕對值。  於溢位時， `_cabs` 傳回 `HUGE_VAL` 和 `errno` 設為 `ERANGE`。  您可以修改 [\_matherr](../../c-runtime-library/reference/matherr.md)以變更錯誤處理。  
  
## 備註  
 `_cabs` 函式會計算複數的絕對值，型別必須為 [\_complex](../../c-runtime-library/standard-types.md)結構。  `z` 結構是由實數元件 `x` 和虛數元件 `y`組成。  對 `_cabs` 的呼叫會產生等於該運算式 `sqrt``z.x``*``z.x` `+` `z.y`\(`z.y` 的值。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_cabs`|\<math.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_cabs.c  
/* Using _cabs, this program calculates  
 * the absolute value of a complex number.  
 */  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   struct _complex number = { 3.0, 4.0 };  
   double d;  
  
   d = _cabs( number );  
   printf( "The absolute value of %f + %fi is %f\n",  
           number.x, number.y, d );  
}  
```  
  
  **The absolute value of 3.000000 \+ 4.000000i is 5.000000**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [abs、 實驗室、 llabs、 \_abs64](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)   
 [fabs、 fabsf fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [labs、llabs](../../misc/labs-llabs.md)