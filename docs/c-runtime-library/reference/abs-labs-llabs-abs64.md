---
title: "abs、 實驗室、 llabs、 _abs64 | Microsoft Docs"
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
  - "abs"
  - "_abs64"
  - "labs"
  - "llabs"
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
  - "stdlib/_abs64"
  - "math/abs"
  - "_abs64"
  - "abs"
  - "labs"
  - "math/labs"
  - "llabs"
  - "math/llabs"
  - "cmath/abs"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "絕對值"
  - "abs 函式"
  - "abs64 函式"
  - "_abs64 函式"
  - "計算絕對值"
ms.assetid: 60f789d1-4a1e-49f5-9e4e-0bdb277ea26a
caps.latest.revision: 29
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# abs、 實驗室、 llabs、 _abs64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算引數的絕對值。  
  
## 語法  
  
```  
int abs(   
   int n   
);  
long abs(   
   long n   
);   // C++ only  
long long abs(   
   long long n   
);   // C++ only  
double abs(   
   double n   
);   // C++ only  
long double abs(  
   long double n  
);   // C++ only  
float abs(  
   float n   
);   // C++ only  
long labs(  
   long n   
);  
long long llabs(  
   long long n   
);  
__int64 _abs64(   
   __int64 n   
);  
```  
  
#### 參數  
 `n`  
 數字值。  
  
## 傳回值  
 `abs`, ，`labs`, ，`llabs` 和 `_abs64` 函式會傳回參數的絕對值 `n`。 不會傳回錯誤。  
  
## 備註  
 因為 c \+ \+ 允許多載，所以您可以呼叫的多載 `abs` 採用並傳回 `long`, ，`long long`, ，`float`, ，`double`, ，和 `long double` 值。 這些多載會定義在 \< h \> 標頭。 在 C 程式中， `abs` 一律採用並傳回 int。  
  
 **Microsoft 特定的**  
  
 由於負數的整數，可以使用任何整數類資料類型表示的範圍是大於可使用該型別表示的整數範圍，就可以提供引數無法轉換這些函式。 如果無法傳回的型別，表示引數的絕對值 `abs` 函式會傳回未變更的引數值。 具體來說， `abs(INT_MIN)` 傳回 `INT_MIN`, ，`labs(LONG_MIN)` 傳回 `LONG_MIN`, ，`llabs(LLONG_MIN)` 傳回 `LLONG_MIN`, ，和 `_abs64(_I64_MIN)` 傳回 `_I64_MIN`。 這表示， `abs` 函數不能保證為正整數值。  
  
 **結束 Microsoft 專有**  
  
## 需求  
  
|常式|必要的 C 標頭|必要的 c \+ \+ 標頭|  
|--------|--------------|--------------------|  
|`abs`, `labs`, `llabs`|\< h.h \> 或 \< stdlib.h \>|\< h \>，\< cstdlib \>，\< stdlib.h \> 或 \< h.h \>|  
|`_abs64`|\<stdlib.h\>|\< d l i b \> 或 \< stdlib.h \>|  
  
 若要使用的多載的版本 `abs` c \+ \+ 中，您必須包含 \< h \> 標頭。  
  
## 範例  
 此程式會計算並顯示數個數字的絕對值。  
  
```c  
// crt_abs.c  
// Build: cl /W3 /TC crt_abs.c  
// This program demonstrates the use of the abs function  
// by computing and displaying the absolute values of  
// several numbers.  
  
#include <stdio.h>  
#include <math.h>  
#include <stdlib.h>  
#include <limits.h>  
  
int main( void )  
{  
    int ix = -4;  
    long lx = -41567L;  
    long long llx = -9876543210LL;  
    __int64 wx = -1;  
  
    // absolute 32 bit integer value  
    printf_s("The absolute value of %d is %d\n", ix, abs(ix));  
  
    // absolute long integer value  
    printf_s("The absolute value of %ld is %ld\n", lx, labs(lx));  
  
    // absolute long long integer value  
    printf_s("The absolute value of %lld is %lld\n", llx, llabs(llx));  
  
    // absolute 64 bit integer value  
    printf_s("The absolute value of 0x%.16I64x is 0x%.16I64x\n", wx,   
        _abs64(wx));  
  
    // Integer error cases:  
    printf_s("Microsoft implementation-specific results:\n");  
    printf_s(" abs(INT_MIN) returns %d\n", abs(INT_MIN));  
    printf_s(" labs(LONG_MIN) returns %ld\n", labs(LONG_MIN));  
    printf_s(" llabs(LLONG_MIN) returns %lld\n", llabs(LLONG_MIN));  
    printf_s(" _abs64(_I64_MIN) returns 0x%.16I64x\n", _abs64(_I64_MIN));  
}  
```  
  
```Output  
為-4 的絕對值是的 4-41567 絕對值是的 41567-9876543210 絕對值是的 9876543210 0xffffffffffffffff 的絕對值是 0x0000000000000001 Microsoft 特定實作的搜尋結果︰ abs(INT_MIN) 傳回介於-2147483648 labs(LONG_MIN) 傳回介於-2147483648 llabs(LLONG_MIN) 傳回-9223372036854775808 _abs64(_I64_MIN) 傳回 0x8000000000000000  
  
```  
  
## .NET Framework 對等用法  
 [System::Math::Abs](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [\_cabs](../../c-runtime-library/reference/cabs.md)   
 [fabs、 fabsf fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [imaxabs](../../c-runtime-library/reference/imaxabs.md)