---
title: "rand_s | Microsoft Docs"
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
  - "rand_s"
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
  - "rand_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "密碼編譯安全的亂數"
  - "產生虛擬亂數"
  - "數字, 產生虛擬隨機"
  - "數字, 虛擬隨機"
  - "虛擬亂數"
  - "rand_s 函式"
  - "亂數, 密碼編譯安全的"
  - "亂數, 產生"
ms.assetid: d6a0be60-997d-4904-8411-8aea6839cc94
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# rand_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

產生虛擬亂數。  這是 [rand](../../c-runtime-library/reference/rand.md) 的安全性增強版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
errno_t rand_s(   unsigned int* randomValue);  
```  
  
## 傳回值  
 如果成功則為零，否則，為錯誤碼。  如果輸入指標`randomValue` 是無效的檔案指標，這些函式叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，此函式回傳 `EINVAL` 並設置 `errno` 為 `EINVAL` 。  如果函式為任何其他原因而失敗， \*`randomValue` 設為 0。  
  
## 備註  
 `rand_s` 函式會在範圍 0 撰寫的虛擬隨機整數給 `UINT_MAX` 給輸入指標。  `rand_s` 函式使用作業系統加密安全產生亂數。  它不會使用 [srand](../../c-runtime-library/reference/srand.md) 函式所產生的種子，也不會影響 `rand`使用的亂數序列。  
  
 `rand_s` 函式在下列範例中要求 `_CRT_RAND_S` 常數定義在要宣告的函式包括陳述式之前，:  
  
```  
#define _CRT_RAND_S  
#include <stdlib.h>  
```  
  
 `rand_s` 是由 [RtlGenRandom](http://msdn.microsoft.com/library/windows/desktop/aa387694) 應用程式開發介面，只能在 Windows XP \(含\) 以後版本可供使用。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`rand_s`|\<stdlib.h\>|  
  
 如需詳細的相容性資訊，請參閱[Compatibility](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_rand_s.c  
// This program illustrates how to generate random  
// integer or floating point numbers in a specified range.  
  
// Remembering to define _CRT_RAND_S prior  
// to inclusion statement.  
#define _CRT_RAND_S  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <limits.h>  
  
int main( void )  
{  
    int             i;  
    unsigned int    number;  
    double          max = 100.0;  
    errno_t         err;  
  
    // Display 10 random integers in the range [ 1,10 ].  
    for( i = 0; i < 10;i++ )  
    {  
        err = rand_s( &number );  
        if (err != 0)  
        {  
            printf_s("The rand_s function failed!\n");  
        }  
        printf_s( "  %u\n", (unsigned int) ((double)number /  
                       ((double) UINT_MAX + 1 ) * 10.0) + 1);  
    }  
  
    printf_s("\n");  
  
    // Display 10 random doubles in [0, max).  
    for (i = 0; i < 10;i++ )  
    {  
        err = rand_s( &number );  
        if (err != 0)  
        {  
            printf_s("The rand_s function failed!\n");  
        }  
        printf_s( "  %g\n", (double) number /   
                          ((double) UINT_MAX + 1) * max );  
    }  
}  
```  
  
## 範例輸出  
  
```  
10  
4  
5  
2  
8  
2  
5  
6  
1  
1  
  
32.6617  
29.4471  
11.5413  
6.41924  
20.711  
60.2878  
61.0094  
20.1222  
80.9192  
65.0712  
```  
  
## .NET Framework 對等用法  
 [System::Random 類別](https://msdn.microsoft.com/en-us/library/system.random.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [srand](../../c-runtime-library/reference/srand.md)