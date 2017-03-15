---
title: "編譯器錯誤 C3915 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3915"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3915"
ms.assetid: 2b0a5e5f-3aec-4a4b-9157-233031817084
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C3915
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' 沒有預設索引的屬性 \(類別索引子\)  
  
 型別沒有預設索引的屬性。  
  
 如需詳細資訊，請參閱[屬性](../../windows/property-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3915。  
  
```  
// C3915.cpp  
// compile with: /clr  
ref class X {  
public:  
// uncomment property to resolve this C3915  
//   property int default[]  
//   {  
//      int get(int i)  
//      {  
//         return 863;  
//      }  
//   }  
};  
  
int main() {  
   X^ x = new X;  
   System::Console::WriteLine(x[1]);   // C3915  
}  
```  
  
## 範例  
 如果您嘗試在用 <xref:System.Reflection.DefaultMemberAttribute> 定義索引子的編譯中使用預設索引子，也可能會發生 C3915。  
  
 下列範例會產生 C3915。  
  
```  
// C3915_b.cpp  
// compile with: /clr  
using namespace System;  
  
[Reflection::DefaultMember("XXX")]  
ref struct A {  
   property Double XXX[Double] {  
      Double get(Double data) {  
         return data*data;  
      }  
   }  
};  
  
ref struct B {  
   property Double default[Double] {  
      Double get(Double data) {  
         return data*data;  
      }  
   }  
};  
  
int main() {  
   A ^ mya = gcnew A();  
   Console::WriteLine("{0}", mya[3]);   // C3915  
  
   B ^ myb = gcnew B();  
   Console::WriteLine("{0}", myb[3]);   // OK  
}  
```