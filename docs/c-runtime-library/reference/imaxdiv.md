---
title: "imaxdiv | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "imaxdiv"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "imaxdiv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "imaxdiv 函式"
ms.assetid: 7d90126f-fdc2-4986-9cdf-94e4c9123d26
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# imaxdiv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將兩個任何大小整數值的商數及餘數當做單一運算來計算。  
  
## 語法  
  
```  
imaxdiv_t imaxdiv(   
   intmax_t numer,  
   intmax_t denom   
);   
```  
  
#### 參數  
 `numer`  
 分子。  
  
 `denom`  
 分母。  
  
## 傳回值  
 使用屬於類型 [intmax\_t](../../c-runtime-library/standard-types.md) 的引數所呼叫的 `imaxdiv` 會傳回屬於類型 [imaxdiv\_t](../../c-runtime-library/standard-types.md) 的結構，這個結構包含商數和餘數。  
  
## 備註  
 `imaxdiv` 函式會將 `denom` 除以 `numer`，因此計算其商數和餘數。  `imaxdiv_t` 結構包含商數 `intmax_t` `quot` 和餘數 `intmax_t` `rem`。  商數的符號與數學商數的符號相同。  其絕對值是小於數學商數絕對值的最大整數。  如果分母為 0，則程式會終止並出現錯誤訊息。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`imaxdiv`|\<inttypes.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_imaxdiv.c  
// Build using: cl /W3 /Tc crt_imaxdiv.c  
// This example takes two integers as command-line  
// arguments and calls imaxdiv to divide the first   
// argument by the second, then displays the results.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <inttypes.h>  
  
int main(int argc, char *argv[])  
{  
   intmax_t x,y;  
   imaxdiv_t div_result;  
  
   x = atoll(argv[1]);  
   y = atoll(argv[2]);  
  
   printf("The call to imaxdiv(%lld, %lld)\n", x, y);  
   div_result = imaxdiv(x, y);  
   printf("results in a quotient of %lld, and a remainder of %lld\n\n",  
          div_result.quot, div_result.rem);  
}  
```  
  
 當建置後，使用 `9460730470000000 8766` 命令列參數呼叫時，程式碼會產生這個輸出：  
  
  **呼叫 imaxdiv\(9460730470000000, 8766\)。**  
**導致商數 1079252848505 和餘數 5170**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [div](../../c-runtime-library/reference/div.md)   
 [ldiv、lldiv](../../c-runtime-library/reference/ldiv-lldiv.md)