---
title: "編譯器警告 (層級 1) C4927 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4927"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4927"
ms.assetid: 7009e740-a2ef-4130-96ba-482e092f717a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4927
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不合法的轉換；已經隱含套用超過一個使用者定義的轉換  
  
 已有超過一個的使用者定義轉換隱含地套用至單一值 \-\- 編譯器並未發現明確轉換，但是發現它曾用過的轉換。  
  
 下列範例會產生 C4927：  
  
```  
// C4927.cpp  
// compile with: /W1  
struct B  
{  
   operator int ()  
   {  
      return 0;  
   }  
};  
  
struct A  
{  
   A(int i)  
   {  
   }  
  
   /*  
   // uncomment this constructor to resolve  
   A(B b)  
   {  
   }  
   */  
};  
  
A f1( B& b)  
{  
   return A(b);  
}  
  
B& f2( B& b)  
{  
   return b;  
}  
  
A f()  
{  
   B b;  
   return A(b);   // ok  
   return f1(b);  // ok  
   return b;      // C4927  
   return B(b);   // C4927  
   return f2(b);  // C4927  
}  
  
int main()  
{  
   B b;  
   A a = b;  
   A a2(b);  
}  
```