---
title: "編譯器錯誤 C2885 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2885"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2885"
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# 編譯器錯誤 C2885
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class::identifier': 在非類別範圍不是有效的 using 宣告  
  
 [using](../../cpp/using-declaration.md) 宣告的使用不正確。  
  
## 範例  
 對 Visual C\+\+ 2005 完成一致性處理後可能會產生這項錯誤：讓 `using` 宣告至巢狀型別已不再有效；您必須明確限定至巢狀型別的各個參考，將型別置於命名空間中，或是建立 typedef。  
  
 下列範例會產生 C2885。  
  
```  
// C2885.cpp  
namespace MyNamespace {  
   class X1 {};  
}  
  
struct MyStruct {  
   struct X1 {  
      int i;  
   };  
};  
  
int main () {  
   using MyStruct::X1;   // C2885  
  
   // OK  
   using MyNamespace::X1;  
   X1 myX1;  
  
   MyStruct::X1 X12;  
  
   typedef MyStruct::X1 abc;  
   abc X13;  
   X13.i = 9;  
}  
```  
  
## 範例  
 如果您將 `using` 關鍵字和類別成員一起使用，則 C\+\+ 會要求您在另一個類別 \(衍生類別\) 之中定義該成員。  
  
 下列範例會產生 C2885。  
  
```  
// C2885_b.cpp  
// compile with: /c  
class A {  
public:  
   int i;  
};  
  
void z() {  
   using A::i;   // C2885 not in a class  
}  
  
class B : public A {  
public:  
   using A::i;  
};  
```