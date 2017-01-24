---
title: "or | Microsoft Docs"
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
  - "std::or"
  - "std.or"
  - "Or"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "or 函式"
ms.assetid: 6523b3ac-0a18-44ec-9e9a-b9bab8525ead
caps.latest.revision: 12
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# or
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

&#124;&#124; 運算子的替代項目。  
  
## 語法  
  
```  
  
#define or ||  
  
```  
  
## 備註  
 巨集會產生 &#124;&#124; 運算子。  
  
## 範例  
  
```  
// iso646_or.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iso646.h>  
  
int main( )  
{  
   using namespace std;  
   bool a = true, b = false, result;  
  
   boolalpha(cout);  
  
   result= a || b;  
   cout << result << endl;  
  
   result= a or b;  
   cout << result << endl;  
}  
```  
  
  **true**  
**true**   
## 需求  
 **標頭：** \<iso646.h\>