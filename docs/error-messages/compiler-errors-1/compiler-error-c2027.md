---
title: "編譯器錯誤 C2027 | Microsoft Docs"
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
  - "C2027"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2027"
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2027
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用未定義型別 'type'  
  
 型別必須定義過才能使用。  若要解決這種錯誤，請先完全定義該型別後再參考它。  
  
## 範例  
 下列範例會產生 C2027。  
  
```  
// C2027.cpp  
class C;  
class D {  
public:  
   void func() {  
   }  
};  
  
int main() {  
   C *pC;  
   pC->func();   // C2027  
  
   D *pD;  
   pD->func();  
}  
```  
  
## 範例  
 是可能宣告指標至已宣告但未定義的型別。但是 Visual C\+\+ 不允許未定義型別的參考。  
  
 下列範例會產生 C2027。  
  
```  
// C2027_b.cpp  
class A;  
A& CreateA();  
  
class B;  
B* CreateB();  
  
int main() {  
   CreateA();   // C2027  
   CreateB();   // OK  
}  
```