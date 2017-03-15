---
title: "編譯器錯誤 C2352 | Microsoft Docs"
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
  - "C2352"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2352"
ms.assetid: 0efad8cb-659f-4b3e-8f6f-9f8ec44d345c
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2352
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class::function'：非靜態成員函式的不合法呼叫  
  
 `static` 成員函式呼叫非靜態成員函式。  或者，從此類別外呼叫非靜態成員函式做為靜態函式。  
  
 下列範例會產生 C2352，並顯示如何修正此問題：  
  
```  
// C2352.cpp  
// compile with: /c  
class CMyClass {  
public:  
   static void func1();  
   void func2();  
   static void func3() {  
      func2();   // C2352 calls nonstatic func2  
      func1();   // OK calls static func1  
   }  
};  
```  
  
 下列範例會產生 C2352，並顯示如何修正此問題：  
  
```  
// C2352b.cpp  
class MyClass {  
public:  
   void MyFunc() {}  
   static void MyFunc2() {}  
};  
  
int main() {  
   MyClass::MyFunc();   // C2352  
   MyClass::MyFunc2();   // OK  
}  
```