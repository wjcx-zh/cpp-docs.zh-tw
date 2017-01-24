---
title: "not_eq | Microsoft Docs"
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
  - "not_eq"
  - "std::not_eq"
  - "std.not_eq"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "not_eq 函式"
ms.assetid: d87ad299-8b50-4393-a57f-06f70e1f23fb
caps.latest.revision: 12
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# not_eq
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\!\= 運算子的替代項目。  
  
## 語法  
  
```  
  
#define not_eq !=  
  
```  
  
## 備註  
 巨集會產生 \!\= 運算子。  
  
## 範例  
  
```  
// iso646_not_eq.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iso646.h>  
  
int main( )  
{  
   using namespace std;  
   int a = 0, b = 1;  
  
   if (a != b)  
      cout << "a is not equal to b" << endl;  
  
   if (a not_eq b)  
      cout << "a is not equal to b" << endl;  
}  
```  
  
  **a 不等於 b。**  
**a 不等於 b。**   
## 需求  
 **標頭：** \<iso646.h\>