---
title: "編譯器錯誤 C3767 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3767"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3767"
ms.assetid: 5247cdcd-639c-4527-bd37-37e74c4e8fab
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 編譯器錯誤 C3767
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 無法存取候選函式  
  
 在類別中定義的 friend 函式，不應視如在全域命名空間範圍中定義和宣告。  不過，可透過與引數相關的查閱去找到。  
  
 某項重大變更也可能會造成 C3767：在 **\/clr** 編譯作業中，原生型別現在預設是私用型別；如需詳細資訊，請參閱[類型可視性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)。  
  
 下列範例會產生 C3767：  
  
```  
// C3767a.cpp  
// compile with: /clr  
using namespace System;  
public delegate void TestDel();  
  
public ref class MyClass {  
public:  
   static event TestDel^ MyClass_Event;  
};  
  
public ref class MyClass2 : public MyClass {  
public:  
   void Test() {  
      MyClass^ patient = gcnew MyClass;  
      patient->MyClass_Event();  
    }  
};  
  
int main() {  
   MyClass^ x = gcnew MyClass;  
   x->MyClass_Event();   // C3767  
  
   // OK  
   MyClass2^ y = gcnew MyClass2();  
   y->Test();  
};  
```  
  
 下列範例會產生 C3767：  
  
```  
// C3767b.cpp  
// compile with: /clr:oldSyntax  
using namespace System;  
__delegate void TestDel();  
  
public __gc class MyClass {  
public:  
   static __event TestDel * MyClass_Event;  
};  
  
public __gc class MyClass2 : public MyClass {  
public:  
   void Test() {  
      MyClass* patient = new MyClass;  
      patient->MyClass_Event();  
    }  
};  
  
int main() {  
   MyClass* x = new MyClass;  
   x->MyClass_Event();   // C3767  
  
   // OK  
   MyClass2 * y = new MyClass2();  
   y->Test();  
};  
```  
  
 下列範例會產生 C3767：  
  
```  
// C3767c.cpp  
// compile with: /clr /c  
  
ref class Base  {  
protected:  
   void Method() {  
      System::Console::WriteLine("protected");  
   }  
};  
  
ref class Der : public Base {  
   void Method() {  
      ((Base^)this)->Method();   // C3767  
      // try the following line instead  
      // Base::Method();  
   }  
};  
```  
  
 下列範例會產生 C3767：  
  
```  
// C3767d.cpp  
// compile with: /clr:oldSyntax /c  
  
__gc class Base {  
protected:  
   void Method() {  
      System::Console::WriteLine("protected");  
   }  
};  
  
__gc class Der : public Base {  
   void Method() {  
      ((Base*)this)->Method();   // C3767  
      // try the following line instead  
      // Base::Method();  
   }  
};  
```  
  
 在 Visual C\+\+ .NET 2002 中，編譯器已改變查閱符號的方法。  原本在某些情況下，它會自動尋找特定命名空間中的符號。  現在，它將使用與引數相關的查閱。  
  
 下列範例會產生 C3767：  
  
```  
// C3767e.cpp  
namespace N {  
   class C {  
      friend void FriendFunc() {}  
      friend void AnotherFriendFunc(C* c) {}  
   };  
}  
  
int main() {  
   using namespace N;  
   FriendFunc();   // C3767 error  
   C* pC = new C();  
   AnotherFriendFunc(pC);   // found via argument-dependent lookup  
}  
```  
  
 對於在 Visual C\+\+ .NET 2003 和 Visual C\+\+ .NET 2002 中有效的程式碼，請在類別中宣告 friend，然後在命名空間範圍中加以定義。  
  
```  
// C3767f.cpp  
class MyClass {  
   int m_private;  
   friend void func();  
};  
  
void func() {  
   MyClass s;  
   s.m_private = 0;  
}  
  
int main() {  
   func();  
}  
```