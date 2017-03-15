---
title: "__min | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__min"
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
  - "__min"
  - "min"
  - "_min"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__min 巨集"
  - "_min 巨集"
  - "min 巨集"
  - "minimum 巨集"
ms.assetid: 2037f26c-b48a-4a69-8870-22519f052a3c
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# __min
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回兩個較小的值。  
  
## 語法  
  
```  
type __min(  
   type a,  
   type b   
);  
```  
  
#### 參數  
 `type`  
 任何數字資料型別。  
  
 `a, b`  
 欲比較的兩個數值型別資料。  
  
## 傳回值  
 較小的兩個引數。  
  
## 備註  
 `__min` 巨集比較兩個數值並回傳較小者的數值。  參數可以是任何數值型別資料，有號或無號。  兩個引數和回傳值都必須是相同的資料型別。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`__min`|\<stdlib.h\>|  
  
## 範例  
  
```  
// crt_minmax.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int a = 10;  
   int b = 21;  
  
   printf( "The larger of %d and %d is %d\n",  a, b, __max( a, b ) );  
   printf( "The smaller of %d and %d is %d\n", a, b, __min( a, b ) );  
}  
```  
  
  **The larger of 10 and 21 is 21**  
**The smaller of 10 and 21 is 10**   
## .NET Framework 對等用法  
 [System::Math::Min](https://msdn.microsoft.com/en-us/library/system.math.min.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [\_\_max](../../c-runtime-library/reference/max.md)