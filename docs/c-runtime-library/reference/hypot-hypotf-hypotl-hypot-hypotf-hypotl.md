---
title: "hypot、hypotf、hypotl、_hypot、_hypotf、_hypotl | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_hypotf"
  - "hypot"
  - "hypotf"
  - "_hypot"
  - "_hypotl"
  - "hypotl"
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
  - "hypotf"
  - "hypotl"
  - "_hypotl"
  - "hypot"
  - "_hypot"
  - "_hypotf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_hypot 函式"
  - "計算斜邊"
  - "hypot 函式"
  - "斜邊計算"
  - "hypotf 函式"
  - "hypotl 函式"
  - "三角形, 計算斜邊"
ms.assetid: 6a13887f-bd53-43fc-9d77-5b42d6e49925
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# hypot、hypotf、hypotl、_hypot、_hypotf、_hypotl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算直角三角形的斜邊。  
  
## 語法  
  
```  
double hypot(   
   double x,  
   double y   
);  
float hypotf(   
   float x,  
   float y   
);  
long double hypotl(  
   long double x,  
   long double y  
);  
double _hypot(   
   double x,  
   double y   
);  
float _hypotf(   
   float x,  
   float y   
);  
long double _hypotl(  
   long double x,  
   long double y  
);  
```  
  
#### 參數  
 `x`, `y`  
 浮點數的值。  
  
## 傳回值  
 如果成功，則 `hypot` 會傳回斜邊的長度；若溢位， `hypot` 會傳回 INF \(無限大\)，而且 `errno` 變數會設定為 `ERANGE`。  您可以使用 `_matherr` 修改錯誤處理。  
  
 如需傳回碼的詳細資訊，請參閱[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 給定直角三角形的兩邊長 `x` 和 `y`，`hypot` 函式會計算斜邊長度 \(也就是，`x`<sup>2</sup> \+ `y`<sup>2</sup> 的平方根\)。  
  
 具有前置底線的函式是為先前標準提供相容性。  它們的行為與沒有前置底線的版本相同。  建議您在新的程式碼中使用沒有前置底線的版本。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`hypot`, `hypotf`, `hypotl`, `_hypot`, `_hypotf`, `_hypotl`|\<math.h\>|  
  
 如需詳細的相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_hypot.c  
// This program prints the hypotenuse of a right triangle.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 3.0, y = 4.0;  
  
   printf( "If a right triangle has sides %2.1f and %2.1f, "  
           "its hypotenuse is %2.1f\n", x, y, _hypot( x, y ) );  
}  
```  
  
  **如果一個直角三角形的兩個邊為 3.0 和 4.0，其斜邊為 5.0**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [\_cabs](../../c-runtime-library/reference/cabs.md)   
 [\_matherr](../../c-runtime-library/reference/matherr.md)