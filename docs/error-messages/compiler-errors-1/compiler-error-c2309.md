---
title: "編譯器錯誤 C2309 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2309"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2309"
ms.assetid: 6303d5b5-72cf-42b8-92ce-b1eb48e80d48
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2309
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

catch 處理常式必須使用括號括住例外狀況的宣告  
  
 catch 處理常式的型別沒有被括號括住。  
  
 下列範例會產生 C2309：  
  
```  
// C2309.cpp  
// compile with: /EHsc  
#include <eh.h>  
class C {};  
int main() {  
   try {  
      throw "ooops!";  
   }  
   catch C {}   // C2309  
   // try the following line instead  
   // catch( C ) {}  
}  
```