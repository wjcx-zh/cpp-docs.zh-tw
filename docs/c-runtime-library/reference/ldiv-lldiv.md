---
title: "ldiv、lldiv | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "ldiv"
  - "lldiv"
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
  - "ldiv"
  - "lldiv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "計算商數"
  - "計算餘數"
  - "ldiv 函式"
  - "lldiv 函式"
  - "商數, 計算"
  - "餘數計算"
ms.assetid: 68ab5d83-27a4-479c-9d52-d055eb139eca
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# ldiv、lldiv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在一次執行內計算兩個整數的商數和餘數。  
  
## 語法  
  
```  
ldiv_t ldiv(  
   long numer,  
   long denom   
);  
lldiv_t lldiv(  
   long long numer,  
   long long denom   
);  
```  
  
#### 參數  
 `numer`  
 分子。  
  
 `denom`  
 分母。  
  
## 傳回值  
 `ldiv` 會傳回包含這個商數和餘數的結構，其型別為 [ldiv\_t](../../c-runtime-library/standard-types.md)。  `lldiv` 會傳回包含這個商數和餘數的結構，其型別為 [lldiv\_t](../../c-runtime-library/standard-types.md)。  
  
## 備註  
 `ldiv` 和 `lldiv` 函式會將 `numer` 除以 `denom`，計算其商數和餘數。  商數的符號與數學商數的符號相同。  商數的絕對值是小於數學上商數絕對值的最大整數。  如果分母為 0，則程式會終止並出現錯誤訊息。  `ldiv` 和 `lldiv` 與 `div`相同，但是 `ldiv` 的引數和傳回結構的成員的型別都是 `long`，而 `lldiv` 的引數和傳回結構的成員的型別是 `long long`。  
  
 `ldiv_t` 和 `lldiv_t` 結構在 \<stdlib.h\> 中定義。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`ldiv`, `lldiv`|\<stdlib.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_ldiv.c  
  
#include <stdlib.h>  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   long x = 5149627, y = 234879;  
   ldiv_t div_result;  
  
   div_result = ldiv( x, y );  
   printf( "For %ld / %ld, the quotient is ", x, y );  
   printf( "%ld, and the remainder is %ld\n",   
            div_result.quot, div_result.rem );  
}  
```  
  
## Output  
  
```  
For 5149627 / 234879, the quotient is 21, and the remainder is 217168  
```  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [div](../../c-runtime-library/reference/div.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)