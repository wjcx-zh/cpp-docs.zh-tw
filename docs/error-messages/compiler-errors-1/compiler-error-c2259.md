---
title: "編譯器錯誤 C2259 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2259"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2259"
ms.assetid: e458236f-bdea-4786-9aa6-a98d8bffa5f4
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# 編譯器錯誤 C2259
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class' : 無法產生抽象類別  
  
 程式碼宣告了一個抽象類別或結構的執行個體。  
  
 您不能以一個或多個純虛擬函式執行個體化類別或結構。  若要產生衍生類別的物件，衍生類別必須覆寫每個純虛擬函式。  
  
 如需詳細資訊，請參閱[隱含抽象類別](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Implicitly_abstract_classes)。  
  
 下列範例會產生 C2259：  
  
```  
// C2259.cpp  
// compile with: /c  
class V {  
public:  
   void virtual func() = 0;  
};  
class A : public V {};  
class B : public V {  
public:  
   void func();  
};  
V v;  // C2259, V is an abstract class  
A a;  // C2259, A inherits func() as pure virtual  
B b;  // OK, B defines func()  
```  
  
 只要從介面衍生，並在衍生類別中，以公用以外的存取權限實作介面方法，就可能會接到 C2259 錯誤訊息。這是因為編譯器必須有在衍生類別中實作的介面方法，才會有公用存取，所以會發生這種錯誤。  當您以限制更多的存取權限實作介面的成員函式時，編譯器不會將它們視為定義於介面中的介面方法實作，因而使得衍生類別變成抽象類別。  
  
 可能解決這種問題的辦法有兩種：  
  
-   將存取權限變成公用，以便實作方法。  
  
-   使用在衍生類別中實作之介面方法的範圍解析運算子，以介面名稱限定實作的方法名稱。  
  
 在 Visual C\+\+ 2005 中完成一致性處理的結果也可能會產生 C2259，**\/Zc:wchar\_t** 現在預設為開啟。  在這種情況下，C2599 的解決方法有兩種：可以透過用 **\/Zc:wchar\_t\-** 編譯，從舊版取得行為；但最好還是更新型別，讓型別相容。  如需詳細資訊，請參閱 [\/Zc:wchar\_t \(wchar\_t 是原生類型\)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。  
  
 下列範例會產生 C2259：  
  
```  
// C2259b.cpp  
// compile with: /c  
#include <windows.h>   
  
class MyClass {  
public:  
   // WCHAR now typedef'ed to wchar_t  
   virtual void func(WCHAR*) = 0;  
};  
  
class MyClass2 : MyClass {  
public:  
   void func(unsigned short*);  
};  
  
MyClass2 x;   // C2259  
  
// OK  
class MyClass3 {  
public:  
   virtual void func(WCHAR*) = 0;  
   virtual void func2(wchar_t*) = 0;  
   virtual void func3(unsigned short*) = 0;  
};  
  
class MyClass4 : MyClass3 {  
public:  
   void func(WCHAR*) {}  
   void func2(wchar_t*) {}  
   void func3(unsigned short*) {}  
};  
  
MyClass4 y;  
```  
  
 下列範例會產生 C2259：  
  
```  
// C2259c.cpp  
// compile with: /clr  
interface class MyInterface {  
   void MyMethod();  
};  
  
ref class MyDerivedClass: public MyInterface {  
private:  
   // Uncomment the following line to resolve.  
   // public:  
   void MyMethod(){}  
   // or the following line  
   // void MyInterface::MyMethod() {};  
};  
  
int main() {  
   MyDerivedClass^ instance = gcnew MyDerivedClass; // C2259  
}  
```  
  
 下列範例會產生 C2259：  
  
```  
// C2259d.cpp  
// compile with: /clr:oldSyntax  
public __gc __interface MyInterface {  
   void MyMethod();  
};  
  
__gc class MyDerivedClass : public MyInterface {  
// Uncomment the following line to resolve.  
// public:  
   void MyMethod() {};  
   // or the following line  
   // void MyInterface::MyMethod() {};  
};  
  
int main() {  
   MyDerivedClass *instance = new MyDerivedClass();   // C2259  
}  
```