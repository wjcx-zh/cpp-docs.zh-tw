---
title: "interface class  (C++ Component Extensions) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "interface_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interface class keyword"
  - "interface struct keyword"
ms.assetid: 3ccea701-f50b-4da7-ad6b-f0ee1203e2b9
caps.latest.revision: 30
caps.handback.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# interface class  (C++ Component Extensions)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

宣告一個介面如需原生介面的詳細資訊，請參閱[\_\_interface](../cpp/interface.md)。  
  
## 所有執行階段  
 **語法**  
  
```  
  
        interface_access interface class  name :  inherit_access base_interface {};  
interface_access interface struct name :  inherit_access base_interface {};  
```  
  
 **參數**  
  
 *interface\_access*  
 介面的協助工具在組件之外。可能的值為 **public** 和 `private`。`private` 是預設值。巢狀介面不能有 *interface\_access* 規範。  
  
 *name*  
 介面的名稱。  
  
 *inherit\_access*  
 *base\_interface* 的存取範圍。基底介面的唯一允許的協助工具是 `public` \(預設值\)。  
  
 *base\_interface* \(選擇性\)  
 介面 *name*的基底介面。  
  
 **備註**  
  
 **interface struct** 和 **interface class**相等。  
  
 介面可以包含函式、事件和屬性的宣告。所有介面成員都具有公用存取範圍。  介面也可以包含靜態資料成員、函式、事件和屬性，因此這些靜態成員必須在介面定義。  
  
 介面定義類別可能會如何實作。  介面不是類別，而類別只能實作介面。  在類別定義在介面中所宣告的函式，函式會實作，不會被覆寫。  因此，名稱搜尋不包括介面成員。  
  
 衍生自介面的類別或結構必須實作介面所有的成員。  當實作介面 *名稱* 時也必須實作 `base_interface` 的介面清單。  
  
 如需詳細資訊，請參閱：  
  
-   [介面靜態建構函式](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)  
  
-   [Generic Interfaces \(Visual C\+\+\)](../windows/generic-interfaces-visual-cpp.md)  
  
 如需其他 CLR 型別的詳細資訊，請參閱 [類別和結構。](../windows/classes-and-structs-cpp-component-extensions.md)。  
  
 您可以在編譯時檢測型別是否有 `__is_interface_class(``type``)`的介面。  如需詳細資訊，請參閱[Compiler Support for Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
 在開發環境中，您可以反白顯示關鍵字 \(例如 `interface class`\) 並按下 F1，來取得這些關鍵字的 F1 說明。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **備註**  
  
 \(這個語言功能沒有只適用於 Windows 執行階段的備註。\)  
  
### 需求  
 編譯器選項：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **備註**  
  
 \(這個語言功能沒有只適用於 Common Language Runtime 的備註。\)  
  
### 需求  
 編譯器選項：**\/clr**  
  
### 範例  
 **範例**  
  
 下列程式碼範例會示範介面如何定義時鐘函式的行為。  
  
```  
// mcppv2_interface_class.cpp  
// compile with: /clr  
using namespace System;  
  
public delegate void ClickEventHandler(int, double);  
  
// define interface with nested interface  
public interface class Interface_A {  
   void Function_1();  
  
   interface class Interface_Nested_A {  
      void Function_2();  
   };  
};  
  
// interface with a base interface  
public interface class Interface_B : Interface_A {  
   property int Property_Block;  
   event ClickEventHandler^ OnClick;     
   static void Function_3() { Console::WriteLine("in Function_3"); }  
};  
  
// implement nested interface  
public ref class MyClass : public Interface_A::Interface_Nested_A {  
public:  
   virtual void Function_2() { Console::WriteLine("in Function_2"); }  
};  
  
// implement interface and base interface  
public ref class MyClass2 : public Interface_B {  
private:  
   int MyInt;  
  
public:  
   // implement non-static function  
   virtual void Function_1() { Console::WriteLine("in Function_1"); }  
  
   // implement property  
   property int Property_Block {  
      virtual int get() { return MyInt; }  
      virtual void set(int value) { MyInt = value; }  
   }  
   // implement event  
   virtual event ClickEventHandler^ OnClick;  
  
   void FireEvents() {  
      OnClick(7, 3.14159);  
   }  
};  
  
// class that defines method called when event occurs  
ref class EventReceiver {  
public:  
   void OnMyClick(int i, double d) {  
      Console::WriteLine("OnClick: {0}, {1}", i, d);  
   }  
};  
  
int main() {  
   // call static function in an interface  
   Interface_B::Function_3();  
  
   // instantiate class that implements nested interface  
   MyClass ^ x = gcnew MyClass;  
   x->Function_2();  
  
   // instantiate class that implements interface with base interface  
   MyClass2 ^ y = gcnew MyClass2;  
   y->Function_1();  
   y->Property_Block = 8;  
   Console::WriteLine(y->Property_Block);  
  
   EventReceiver^ MyEventReceiver = gcnew EventReceiver();  
  
   // hook handler to event  
   y->OnClick += gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);  
  
   // invoke events  
   y->FireEvents();  
  
   // unhook handler to event  
   y->OnClick -= gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);  
  
   // call implemented function via interface handle  
   Interface_A^ hi = gcnew MyClass2();  
   hi->Function_1();  
}  
```  
  
 **Output**  
  
  **in Function\_3**  
 **in Function\_2**  
 **in Function\_1**  
 **8**  
 **OnClick：7, 3.14159**  
 **in Function\_1** **範例**  
  
 下列程式碼範例顯示兩種實作多重介面宣告的相同簽章的函式，而類別的地方使用這些介面。  
  
```  
// mcppv2_interface_class_2.cpp  
// compile with: /clr /c  
interface class I {  
   void Test();  
   void Test2();  
};  
  
interface class J : I {  
   void Test();  
   void Test2();  
};  
  
ref struct R : I, J {  
   // satisfies the requirement to implement Test in both interfaces  
   virtual void Test() {}  
  
   // implement both interface functions with explicit overrides  
   virtual void A() = I::Test2 {}  
   virtual void B() = J::Test2 {}  
};  
```  
  
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)