---
title: "_STATIC_ASSERT 巨集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
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
apitype: "DLLExport"
f1_keywords: 
  - "_STATIC_ASSERT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_STATIC_ASSERT 巨集"
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _STATIC_ASSERT 巨集
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當結果為 `FALSE`時，請評估運算式在編譯時期並產生錯誤。  
  
## 語法  
  
```  
_STATIC_ASSERT(  
    booleanExpression  
);  
```  
  
#### 參數  
 `booleanExpression`  
 運算式 \(包括指標\) 來評估為非零\(`TRUE`\) 或 0 \(`FALSE`\)。  
  
## 備註  
 這個巨集類似 [\_ASSERT 和 \_ASSERTE 巨集](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)，不過， `booleanExpression` 會在編譯時期而非執行階段。  如果為 `FALSE` \(0\)，以 [編譯器錯誤 C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) 方式將指定的 `booleanExpression` 評估產生。  
  
## 範例  
 在此範例中，要檢查 `sizeof` `int` 是否大於或等於 2 個位元組，而且 `sizeof` `long` 是否為 1 位元組。  程式不會編譯，並產生 [編譯器錯誤 C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) ，因為 `long` 大於 1 個位元組。  
  
```  
// crt__static_assert.c  
  
#include <crtdbg.h>  
#include <stdio.h>  
  
_STATIC_ASSERT(sizeof(int) >= 2);  
_STATIC_ASSERT(sizeof(long) == 1);  // C2466  
  
int main()  
{  
    printf("I am sure that sizeof(int) will be >= 2: %d\n",  
        sizeof(int));  
    printf("I am not so sure that sizeof(long) == 1: %d\n",  
        sizeof(long));  
}  
```  
  
## 需求  
  
|巨集|必要的標頭|  
|--------|-----------|  
|`_STATIC_ASSERT`|\<crtdbg.h\>|  
  
## .NET Framework 對等用法  
 [System::Diagnostics::Debug::Assert](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [\_ASSERT、\_ASSERTE、\_ASSERT\_EXPR 巨集](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)