---
title: "編譯器錯誤 C3673 | Microsoft Docs"
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
  - "C3673"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3673"
ms.assetid: bb6d2079-05af-4e2c-be0e-75c892e6c590
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3673
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : 類別沒有複製建構函式  
  
 需要使用者定義的建構函式，才能複製 CLR ref 型別的物件。  如需詳細資訊，請參閱[參考類型的 C\+\+ 堆疊語意](../../dotnet/cpp-stack-semantics-for-reference-types.md)。  
  
## 範例  
 下列範例會產生 C3673。  
  
```  
// C3673.cpp  
// compile with: /clr  
public ref struct R {  
public:  
   R() {}  
   // Uncomment the following line to resolve.  
   // R(R% p) {}  
};  
  
int main() {  
   R r;  
   R s = r;   // C3673  
}  
```  
  
## 範例  
 下列範例會產生 C3673。  
  
```  
// C3673_b.cpp  
// compile with: /clr /c  
// C3673 expected  
using namespace System;  
[AttributeUsage(AttributeTargets::Class)]  
ref class MyAttr : public Attribute {  
public:  
   MyAttr() {}  
   // Uncomment the following line to resolve.  
   // MyAttr(int i) {}  
   property int Priority;  
   property int Version;  
};  
  
[MyAttr]   
ref class ClassA {};   // OK, no arguments  
  
[MyAttr(Priority = 1)]   
ref class ClassB {};   // OK, named argument  
  
[MyAttr(123)]  
ref class ClassC {};   // Positional argument  
  
[MyAttr(123, Version = 1)]  
ref class ClassD {};   // Positional and named  
```