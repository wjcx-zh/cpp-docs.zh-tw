---
title: interface 類別 (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- interface_CPP
helpviewer_keywords:
- interface class keyword
- interface struct keyword
ms.assetid: 3ccea701-f50b-4da7-ad6b-f0ee1203e2b9
ms.openlocfilehash: 60e8965e3ef2538554d8c664b35bd0849bd5e69e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515703"
---
# <a name="interface-class--ccli-and-ccx"></a>interface 類別 (C++/CLI 和 C++/CX)

宣告介面。  如需原生介面的相關資訊，請參閱 [__interface](../cpp/interface.md)。

## <a name="all-runtimes"></a>所有執行階段

### <a name="syntax"></a>語法

```cpp
interface_access
interface class
name :  inherit_accessbase_interface{};interface_accessinterface structname :  inherit_accessbase_interface{};
```

### <a name="parameters"></a>參數

*interface_access*<br/>
介面在組件外部的可及性。  可能的值為 **public** 和 **private**。  **private** 為預設值。 巢狀介面不能有 *interface_access* 可及性。

*name*<br/>
介面的名稱。

*inherit_access*<br/>
*base_interface* 的可及性。  對於基底介面唯一允許的可及性為 **public** (預設值)。

*base_interface*<br/>
(選擇性) 介面 *name* 的基底介面。

### <a name="remarks"></a>備註

**interface struct** 相當於 **interface class**。

介面可以包含函式、事件和屬性的宣告。  所有介面成員都具有 public 可及性。 介面也可以包含靜態資料成員、函式、事件和屬性，而且這些靜態成員都必須定義於介面中。

介面會定義可能要如何實作類別的方式。 介面不是類別，而類別僅能實作介面。 如果類別會定義介面中所宣告的函式，就會實作該函式，而不會覆寫。 因此，名稱查閱不會包含介面成員。

衍生自介面的類別或結構必須實作介面的所有成員。 實作介面 *name* 時，您也必須實作 `base_interface` 清單中的介面。

如需詳細資訊，請參閱:

- [介面靜態建構函式](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)

- [泛型介面 (C++/CLI)](generic-interfaces-visual-cpp.md)

如需其他 CLR 型別的相關資訊，請參閱[類別和結構](classes-and-structs-cpp-component-extensions.md)。

您可以在編譯時期偵測某個型別是否為具有 `__is_interface_class(type)` 的介面。 如需詳細資訊，請參閱[型別特性的編譯器支援](compiler-support-for-type-traits-cpp-component-extensions.md)。

在開發環境中，您可以透過反白顯示關鍵字 (例如 `interface class`)，然後按 F1 來取得有關這些關鍵字的 F1 說明。

## <a name="windows-runtime"></a>Windows 執行階段

### <a name="remarks"></a>備註

(這個語言功能沒有只適用於 Windows 執行階段的備註。)

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>備註

(這個語言功能沒有只適用於 Common Language Runtime 的備註。)

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

下列程式碼範例示範介面如何定義 clock 函式的行為。

```cpp
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

```Output
in Function_3

in Function_2

in Function_1

8

OnClick: 7, 3.14159

in Function_1
```

下列程式碼範例示範兩種方式，可使用宣告於多個介面中的相同簽章來實作函式，而類別會在哪裡使用那些介面。

```cpp
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

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)