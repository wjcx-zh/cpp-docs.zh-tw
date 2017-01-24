---
title: "bitand | Microsoft Docs"
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
  - "std::bitand"
  - "std.bitand"
  - "bitand"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bitand 函式"
ms.assetid: 279cf9b5-fac1-49de-b329-f1a31b3481fe
caps.latest.revision: 12
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# bitand
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

& 運算子的替代項目。  
  
## 語法  
  
```  
  
#define bitand &  
  
```  
  
## 備註  
 巨集會產生運算子  
  
## 範例  
  
```  
// iso646_bitand.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iso646.h>  
  
int main( )  
{  
   using namespace std;  
   int a = 1, b = 2, result;  
  
   result = a & b;  
   cout << result << endl;  
  
   result= a bitand b;  
   cout << result << endl;  
}  
```  
  
  **0**  
**0**   
## 需求  
 **標頭：** \<iso646.h\>