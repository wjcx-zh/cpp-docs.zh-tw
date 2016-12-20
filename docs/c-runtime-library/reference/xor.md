---
title: "xor | Microsoft Docs"
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
  - "Xor"
  - "std::xor"
  - "std.xor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "xor 函式"
ms.assetid: 0fe9554b-d87b-4487-92ed-366c6dc21df2
caps.latest.revision: 12
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# xor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

^ 運算子的替代項目。  
  
## 語法  
  
```  
  
#define xor ^  
  
```  
  
## 備註  
 巨集會產生 ^ 運算子。  
  
## 範例  
  
```  
// iso646_xor.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iso646.h>  
  
int main( )  
{  
   using namespace std;  
   int a = 3, b = 2, result;  
  
   result= a ^ b;  
   cout << result << endl;  
  
   result= a xor_eq b;  
   cout << result << endl;  
}  
```  
  
  **1**  
**1**   
## 需求  
 **標頭：** \<iso646.h\>