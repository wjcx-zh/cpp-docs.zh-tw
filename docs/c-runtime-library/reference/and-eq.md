---
title: "and_eq | Microsoft Docs"
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
  - "and_eq"
  - "std.and_eq"
  - "std::and_eq"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "and_eq 巨集"
ms.assetid: 11091772-e359-4c2b-95c6-00841ac04354
caps.latest.revision: 12
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# and_eq
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

&\= 運算子的替代項目。  
  
## 語法  
  
```  
  
#define and_eq &=  
  
```  
  
## 備註  
 巨集會產生 &\= 運算子。  
  
## 範例  
  
```  
// iso646_and_eq.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iso646.h>  
  
int main( )  
{  
   using namespace std;  
   int a = 3, b = 2, result;  
  
   result= a &= b;  
   cout << result << endl;  
  
   result= a and_eq b;  
   cout << result << endl;  
}  
```  
  
  **2**  
**2**   
## 需求  
 **標頭：** \<iso646.h\>