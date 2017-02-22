---
title: "編譯器錯誤 C3145 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3145"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3145"
ms.assetid: f165c874-0f51-45c7-85e8-ebe321cbc168
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# 編譯器錯誤 C3145
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'object'：全域或靜態變數不可以有 Managed 或 WinRT 類型 'type'  
  
 您只能在函式範圍內定義 CLR 或 WinRT 物件。  
  
 下列範例會產生 C3145，並說明如何加以修正：  
  
```  
// C3145.cpp  
// compile with: /clr  
using namespace System;   
ref class G {};   
  
G ^ ptr;   // C3145  
G ^ ptr2 = gcnew G;   // C3145  
  
ref class GlobalObjects {  
public:  
   static G ^ ptr;   // OK  
   static G ^ ptr2 = gcnew G;   // OK   
};   
  
int main() {  
   G ^ ptr;   // OK  
   G ^ ptr2 = gcnew G;   // OK  
}  
```  
  
 下列範例會產生 C3145：  
  
```  
// C3145b.cpp  
// compile with: /clr  
ref class MyClass {  
public:  
   static int data;  
};  
  
interior_ptr<int> p = &(MyClass::data);   // C3145  
  
void Test(interior_ptr<int> x) {}  
  
int main() {  
   MyClass ^ h_MyClass = gcnew MyClass;  
   interior_ptr<int> p = &(h_MyClass->data);  
}  
```  
  
 **Managed Extensions for C\+\+**  
  
 下列範例會產生 C3145：  
  
```  
// C3145c.cpp  
// compile with: /clr:oldSyntax  
using namespace System;   
__gc class G {};   
  
G *ptr;   // C3145  
G *ptr2 = new G;   // C3145  
  
__gc class GlobalObjects {  
public:  
   static G *ptr;   // OK  
   static G *ptr2 = new G;   // OK   
};   
  
int main() {  
   G *ptr;   // OK  
   G *ptr2 = new G;   // OK  
}  
```