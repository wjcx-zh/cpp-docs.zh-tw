---
title: 泛型類別 (C++/CLI)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- classes [C++], generic
- generic classes [C++], about generic classes
- data types [C++], generic
- generic classes
- generics [C++], declaring generic classes
ms.assetid: 0beb99e1-1ec4-4fee-9836-ce9657d67a3a
ms.openlocfilehash: 78f4bf3abb98aab5e626e8ada538a22bdbca2912
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172356"
---
# <a name="generic-classes-ccli"></a>泛型類別 (C++/CLI)

泛型類別會使用以下格式需告：

## <a name="syntax"></a>語法

```cpp
[attributes]
generic <class-key type-parameter-identifier(s)>
[constraint-clauses]
[accessibility-modifiers] ref class identifier  [modifiers]
[: base-list]
{
class-body
} [declarators] [;]
```

## <a name="remarks"></a>備註

上述語法中會使用下列詞彙：

*attributes*<br/>
(選擇性) 其他宣告資訊。 如需關於屬性及屬性類別的詳細資訊，請參閱＜屬性＞。

*class-key*<br/>
**class** 或 **typename**

*type-parameter-identifier(s)* ，指定型別參數名稱的識別碼 (以逗號區隔) 清單。

*constraint-clauses*<br/>
指定型別參數條件約束的 **where** 子句 (不以逗號區隔) 清單。 採用以下格式：

> **其中，** *類型參數識別碼* **：** *條件約束清單*  **...**

*constraint-list*<br/>
*類別或介面*[`,` *...* ]

*accessibility-modifiers*<br/>
泛型類別的存取範圍修飾詞。 Windows 執行階段唯一允許的修飾詞為 **private**。 Common Language Runtime 允許的修飾詞為 **private** 和 **public**。

*identifier*<br/>
泛型類別名稱，可以是任何有效的 C++ 識別碼。

*modifiers*<br/>
(選擇性) 允許的修飾詞包括 **sealed** 和 **abstract**。

*base-list*<br/>
包含一個基底類別和任何實作介面 (全部以逗號區隔) 的清單。

*class-body*<br/>
包含欄位、成員函式等項目的類別主體。

*declarators*<br/>
此型別任何變數的宣告。 例如：`^`*identifier*[`,` ...]

您可以宣告這類的泛型類別 (請注意，可使用關鍵字 **class**，不要使用 **typename**)。 在這個範例中，`ItemType`、`KeyType` 和 `ValueType` 是於型別所在點指定的未知型別。 `HashTable<int, int>` 為泛型型別 `HashTable<KeyType, ValueType>` 的建構型別。 您可以自單一泛型型別建構幾個不同的建構型別。 系統會以和任何其他 ref 類別型別相同的方式，處理建構自泛型類別的建構型別。

```cpp
// generic_classes_1.cpp
// compile with: /clr
using namespace System;
generic <typename ItemType>
ref struct Stack {
   // ItemType may be used as a type here
   void Add(ItemType item) {}
};

generic <typename KeyType, typename ValueType>
ref class HashTable {};

// The keyword class may be used instead of typename:
generic <class ListItem>
ref class List {};

int main() {
   HashTable<int, Decimal>^ g1 = gcnew HashTable<int, Decimal>();
}
```

實值型別 (可以是像 **int** 或 **double** 這樣的內建型別，或使用者定義的實值型別) 和參考型別可作為泛型型別引數使用。 無論如何，泛型定義內的語法都是一樣的。 在語法上，未知型別會被視為參考型別。 但執行階段也會判斷實際使用的型別是否為實值型別，並取代適當產生的程式碼以直接存取成員。 作為泛型型別引數使用的實值型別不會進行 boxing 處理，因此不會發生因進行該處理而對效能造成負面影響的問題。 泛型主體內使用的語法應為 `T^` 和`->`，而不是 `.`。 如果型別引數為實值型別，針對型別參數使用的任何 [ref new, gcnew](ref-new-gcnew-cpp-component-extensions.md)，都將由執行階段適當地解譯為簡單的實值型別建立作業。

您也可以在可用於型別參數的型別上，宣告包含[泛型型別參數的條件約束 (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md)的泛型類別。 在以下範例中，所有用於 `ItemType` 的型別都必須實作 `IItem` 介面。 例如嘗試使用 **int**，這不會實作 `IItem`，而是會產生編譯時間錯誤，因為型別引數不符合條件約束。

```cpp
// generic_classes_2.cpp
// compile with: /clr /c
interface class IItem {};
generic <class ItemType>
where ItemType : IItem
ref class Stack {};
```

在相同的命名空間中，無法透過僅變更型別參數的數目或型別的方式來多載泛型類別。 但如果每個類別都位於不同的命名空間，那就可以多載。 例如，假設 `MyClass` 和 `MyClass<ItemType>` 這兩個類別分別位於 `A` 和 `B` 命名空間。 就可以在命名空間 C 中多載該兩個類別：

```cpp
// generic_classes_3.cpp
// compile with: /clr /c
namespace A {
   ref class MyClass {};
}

namespace B {
   generic <typename ItemType>
   ref class MyClass2 { };
}

namespace C {
   using namespace A;
   using namespace B;

   ref class Test {
      static void F() {
         MyClass^ m1 = gcnew MyClass();   // OK
         MyClass2<int>^ m2 = gcnew MyClass2<int>();   // OK
      }
   };
}
```

基底類別和基底介面不能是型別參數。 但基底類別可以包含型別參數做為引數，如以下情況所示：

```cpp
// generic_classes_4.cpp
// compile with: /clr /c
generic <typename ItemType>
interface class IInterface {};

generic <typename ItemType>
ref class MyClass : IInterface<ItemType> {};
```

建構函式和解構函式會針對每個物件執行個體執行一次 (一如往常)；靜態建構函式會針對每個建構的型別執行一次。

## <a name="fields-in-generic-classes"></a>泛型類別中的欄位

本節示範在泛型類別中使用執行個體和靜態欄位的方式。

### <a name="instance-variables"></a>執行個體變數

泛型類別的執行個體變數可以有型別和變數初始設定式，該初始設定式中包括來自封入型別的所有型別參數。

## <a name="example"></a>範例

在以下範例中，會使用適當的型別引數 (\<int **、** double**和**string **) 來建立泛型類別 MyClass**ItemType > 的三個不同執行個體。

```cpp
// generics_instance_fields1.cpp
// compile with: /clr
// Instance fields on generic classes
using namespace System;

generic <typename ItemType>
ref class MyClass {
// Field of the type ItemType:
public :
   ItemType field1;
   // Constructor using a parameter of the type ItemType:
   MyClass(ItemType p) {
   field1 = p;
   }
};

int main() {
   // Instantiate an instance with an integer field:
   MyClass<int>^ myObj1 = gcnew MyClass<int>(123);
   Console::WriteLine("Integer field = {0}", myObj1->field1);

   // Instantiate an instance with a double field:
   MyClass<double>^ myObj2 = gcnew MyClass<double>(1.23);
   Console::WriteLine("Double field = {0}", myObj2->field1);

   // Instantiate an instance with a String field:
   MyClass<String^>^ myObj3 = gcnew MyClass<String^>("ABC");
   Console::WriteLine("String field = {0}", myObj3->field1);
   }
```

```Output
Integer field = 123
Double field = 1.23
String field = ABC
```

## <a name="static-variables"></a>靜態變數

建立新的泛型型別時，會建立任何靜態變數的新執行個體，並執行該型別的任何靜態建構函式。

靜態變數可以使用來自封入類別的任何型別參數。

## <a name="example"></a>範例

以下範例會示範如何在泛型類別內使用靜態欄位和靜態建構函式。

```cpp
// generics_static2.cpp
// compile with: /clr
using namespace System;

interface class ILog {
   void Write(String^ s);
};

ref class DateTimeLog : ILog {
public:
   virtual void Write(String^ s) {
      Console::WriteLine( "{0}\t{1}", DateTime::Now, s);
   }
};

ref class PlainLog : ILog {
public:
   virtual void Write(String^ s) { Console::WriteLine(s); }
};

generic <typename LogType>
where LogType : ILog
ref class G {
   static LogType s_log;

public:
   G(){}
   void SetLog(LogType log) { s_log = log; }
   void F() { s_log->Write("Test1"); }
   static G() { Console::WriteLine("Static constructor called."); }
};

int main() {
   G<PlainLog^>^ g1 = gcnew G<PlainLog^>();
   g1->SetLog(gcnew PlainLog());
   g1->F();

   G<DateTimeLog^>^ g2 = gcnew G<DateTimeLog^>();
   g2->SetLog(gcnew DateTimeLog());

   // prints date
   // g2->F();
}
```

```Output
Static constructor called.
Static constructor called.
Static constructor called.
Test1
```

## <a name="methods-in-generic-classes"></a>泛型類別中的方法

泛型類別中的方法可以是泛型本身；非泛型方法則將透過類別型別參數以隱含方式參數化。

下列特殊規則會套用到泛型類別內的方法：

- 泛型類別中的方法可使用型別參數作為參數、傳回型別或本機變數。

- 泛型類別中的方法可使用開啟或關閉的建構型別作為參數、傳回型別或本機變數。

### <a name="non-generic-methods-in-generic-classes"></a>泛型類別中的非泛型方法

對於沒有任何其他型別參數的泛型類別，其中的方法通常被稱為非泛型方法，雖然它們會透過封入泛型類別以隱含方式參數化。

非泛型方法的簽章可以直接，或以開放式建構型別方式，包含封入類別的一或多個型別參數。 例如：

`void MyMethod(MyClass<ItemType> x) {}`

這類方法的主體也可以使用這些型別參數。

## <a name="example"></a>範例

以下範例會在泛型類別 `ProtectData` 內部，宣告非泛型方法 `MyClass<ItemType>`。 此方法會以開放式建構型別方式，在其簽章中使用類別型別參數 `ItemType`。

```cpp
// generics_non_generic_methods1.cpp
// compile with: /clr
// Non-generic methods within a generic class.
using namespace System;

generic <typename ItemType>
ref class MyClass {
public:
   String^ name;
   ItemType data;

   MyClass(ItemType x) {
      data = x;
   }

   // Non-generic method using the type parameter:
   virtual void ProtectData(MyClass<ItemType>^ x) {
      data = x->data;
   }
};

// ItemType defined as String^
ref class MyMainClass: MyClass<String^> {
public:
   // Passing "123.00" to the constructor:
   MyMainClass(): MyClass<String^>("123.00") {
      name = "Jeff Smith";
   }

   virtual void ProtectData(MyClass<String^>^ x) override {
      x->data = String::Format("${0}**", x->data);
   }

   static void Main() {
      MyMainClass^ x1 = gcnew MyMainClass();

      x1->ProtectData(x1);
      Console::WriteLine("Name: {0}", x1->name);
      Console::WriteLine("Amount: {0}", x1->data);
   }
};

int main() {
   MyMainClass::Main();
}
```

```Output
Name: Jeff Smith
Amount: $123.00**
```

## <a name="generic-methods-in-generic-classes"></a>泛型類別中的泛型方法

泛型和非泛型類別中都可以宣告泛型方法。 例如：

## <a name="example"></a>範例

```cpp
// generics_method2.cpp
// compile with: /clr /c
generic <typename Type1>
ref class G {
public:
   // Generic method having a type parameter
   // from the class, Type1, and its own type
   // parameter, Type2
   generic <typename Type2>
   void Method1(Type1 t1, Type2 t2) { F(t1, t2); }

   // Non-generic method:
   // Can use the class type param, Type1, but not Type2.
   void Method2(Type1 t1) { F(t1, t1); }

   void F(Object^ o1, Object^ o2) {}
};
```

非泛型方法仍然是泛型，因為它是透過類別的型別參數參數化，但它沒有其他型別參數。

泛型類別中方法的所有型別都可以是泛型，包括靜態、執行個體和虛擬方法。

## <a name="example"></a>範例

以下範例會示範如何在泛型類別內宣告及使用泛型方法：

```cpp
// generics_generic_method2.cpp
// compile with: /clr
using namespace System;
generic <class ItemType>
ref class MyClass {
public:
   // Declare a generic method member.
   generic <class Type1>
   String^ MyMethod(ItemType item, Type1 t) {
      return String::Concat(item->ToString(), t->ToString());
   }
};

int main() {
   // Create instances using different types.
   MyClass<int>^ myObj1 = gcnew MyClass<int>();
   MyClass<String^>^ myObj2 = gcnew MyClass<String^>();
   MyClass<String^>^ myObj3 = gcnew MyClass<String^>();

   // Calling MyMethod using two integers.
   Console::WriteLine("MyMethod returned: {0}",
            myObj1->MyMethod<int>(1, 2));

   // Calling MyMethod using an integer and a string.
   Console::WriteLine("MyMethod returned: {0}",
            myObj2->MyMethod<int>("Hello #", 1));

   // Calling MyMethod using two strings.
   Console::WriteLine("MyMethod returned: {0}",
       myObj3->MyMethod<String^>("Hello ", "World!"));

   // generic methods can be called without specifying type arguments
   myObj1->MyMethod<int>(1, 2);
   myObj2->MyMethod<int>("Hello #", 1);
   myObj3->MyMethod<String^>("Hello ", "World!");
}
```

```Output
MyMethod returned: 12
MyMethod returned: Hello #1
MyMethod returned: Hello World!
```

## <a name="using-nested-types-in-generic-classes"></a>在泛型類別中使用巢狀型別

和一般類別一樣，您也可以在泛型類別內部宣告其他型別。 巢狀類別宣告會透過外部類別宣告的型別參數以隱含方式參數化。 因此，會針對每個建構的外部型別定義不同的巢狀類別。 例如在以下宣告中：

```cpp
// generic_classes_5.cpp
// compile with: /clr /c
generic <typename ItemType>
ref struct Outer {
   ref class Inner {};
};
```

型別 `Outer<int>::Inner` 和型別 `Outer<double>::Inner` 不一樣。

和泛型類別中的泛型方法一樣，可以為巢狀型別定義其他型別參數。 如果在內部和外部類別中使用相同的型別參數名稱，內部型別參數將會隱藏外部型別參數。

```cpp
// generic_classes_6.cpp
// compile with: /clr /c
generic <typename ItemType>
ref class Outer {
   ItemType outer_item;   // refers to outer ItemType

   generic <typename ItemType>
   ref class Inner {
      ItemType inner_item;   // refers to Inner ItemType
   };
};
```

因為沒有任何方法能夠參考外部型別參數，編譯器將會在此情況下產生警告。

為建構的巢狀泛型型別命名時，即使內部型別已經透過外部型別的型別參數以隱含方式參數化，外部型別的型別參數也不會納入內部型別的型別參數清單中。 在上述案例中，建構型別的名稱會是 `Outer<int>::Inner<string>`。

以下範例會示範如何在泛型類別中，建置及讀取使用巢狀型別連結的清單。

## <a name="example"></a>範例

```cpp
// generics_linked_list.cpp
// compile with: /clr
using namespace System;
generic <class ItemType>
ref class LinkedList {
// The node class:
public:
   ref class Node {
   // The link field:
   public:
      Node^ next;
      // The data field:
      ItemType item;
   } ^first, ^current;
};

ref class ListBuilder {
public:
   void BuildIt(LinkedList<double>^ list) {
      /* Build the list */
      double m[5] = {0.1, 0.2, 0.3, 0.4, 0.5};
      Console::WriteLine("Building the list:");

      for (int n=0; n<=4; n++) {
         // Create a new node:
         list->current = gcnew LinkedList<double>::Node();

         // Assign a value to the data field:
         list->current->item = m[n];

         // Set the link field "next" to be the same as
         // the "first" field:
         list->current->next = list->first;

         // Redirect "first" to the new node:
         list->first = list->current;

         // Display node's data as it builds:
         Console::WriteLine(list->current->item);
      }
   }

   void ReadIt(LinkedList<double>^ list) {
      // Read the list
      // Make "first" the "current" link field:
      list->current = list->first;
      Console::WriteLine("Reading nodes:");

      // Read nodes until current == null:
      while (list->current != nullptr) {
         // Display the node's data field:
         Console::WriteLine(list->current->item);

         // Move to the next node:
         list->current = list->current->next;
      }
   }
};

int main() {
   // Create a list:
   LinkedList<double>^ aList = gcnew LinkedList<double>();

   // Initialize first node:
   aList->first = nullptr;

   // Instantiate the class, build, and read the list:
   ListBuilder^ myListBuilder = gcnew ListBuilder();
   myListBuilder->BuildIt(aList);
   myListBuilder->ReadIt(aList);
}
```

```Output
Building the list:
0.1
0.2
0.3
0.4
0.5
Reading nodes:
0.5
0.4
0.3
0.2
0.1
```

## <a name="properties-events-indexers-and-operators-in-generic-classes"></a>泛型類別中的屬性、事件、索引子和運算子

- 屬性、事件、索引子和運算子可以使用封入泛型型別的型別參數作為傳回值、參數，或區域變數，例如當 `ItemType` 為類別的型別參數時：

    ```cpp
    public ItemType MyProperty {}
    ```

- 屬性、事件、索引子和運算子本身無法參數化。

## <a name="example"></a>範例

這個範例會示範如何在泛型類別內宣告執行個體屬性。

```cpp
// generics_generic_properties1.cpp
// compile with: /clr
using namespace System;

generic <typename ItemType>
ref class MyClass {
private:
   property ItemType myField;

public:
   property ItemType MyProperty {
      ItemType get() {
         return myField;
      }
      void set(ItemType value) {
         myField = value;
      }
   }
};

int main() {
   MyClass<String^>^ c = gcnew MyClass<String^>();
   MyClass<int>^ c1 = gcnew MyClass<int>();

   c->MyProperty = "John";
   c1->MyProperty = 234;

   Console::Write("{0}, {1}", c->MyProperty, c1->MyProperty);
}
```

```Output
John, 234
```

## <a name="example"></a>範例

下一個範例將說明包含事件的泛型類別。

```cpp
// generics_generic_with_event.cpp
// compile with: /clr
// Declare a generic class with an event and
// invoke events.
using namespace System;

// declare delegates
generic <typename ItemType>
delegate void ClickEventHandler(ItemType);

// generic class that defines events
generic <typename ItemType>
ref class EventSource {
public:
   // declare the event OnClick
   event ClickEventHandler<ItemType>^ OnClick;
   void FireEvents(ItemType item) {
      // raises events
      OnClick(item);
   }
};

// generic class that defines methods that will called when
// event occurs
generic <typename ItemType>
ref class EventReceiver {
public:
   void OnMyClick(ItemType item) {
   Console::WriteLine("OnClick: {0}", item);
   }
};

int main() {
   EventSource<String^>^ MyEventSourceString =
                   gcnew EventSource<String^>();
   EventSource<int>^ MyEventSourceInt = gcnew EventSource<int>();
   EventReceiver<String^>^ MyEventReceiverString =
                   gcnew EventReceiver<String^>();
   EventReceiver<int>^ MyEventReceiverInt = gcnew EventReceiver<int>();

   // hook handler to event
   MyEventSourceString->OnClick += gcnew ClickEventHandler<String^>(
       MyEventReceiverString, &EventReceiver<String^>::OnMyClick);
   MyEventSourceInt->OnClick += gcnew ClickEventHandler<int>(
             MyEventReceiverInt, &EventReceiver<int>::OnMyClick);

   // invoke events
   MyEventSourceString->FireEvents("Hello");
   MyEventSourceInt->FireEvents(112);

   // unhook handler to event
   MyEventSourceString->OnClick -= gcnew ClickEventHandler<String^>(
        MyEventReceiverString, &EventReceiver<String^>::OnMyClick);
   MyEventSourceInt->OnClick -= gcnew ClickEventHandler<int>(
        MyEventReceiverInt, &EventReceiver<int>::OnMyClick);
}
```

## <a name="generic-structs"></a>泛型結構

除了 Visual C++ 語言參考中提到的差異之外，泛型結構的宣告和使用規則與泛型類別相同。

## <a name="example"></a>範例

以下範例會宣告泛型結構 `MyGenStruct`，其中包含一個欄位 `myField`，並將不同型別 (**int**、**double** 和 `String^`) 的值指派給此欄位。

```cpp
// generics_generic_struct1.cpp
// compile with: /clr
using namespace System;

generic <typename ItemType>
ref struct MyGenStruct {
public:
   ItemType myField;

   ItemType AssignValue(ItemType item) {
      myField = item;
      return myField;
   }
};

int main() {
   int myInt = 123;
   MyGenStruct<int>^ myIntObj = gcnew MyGenStruct<int>();
   myIntObj->AssignValue(myInt);
   Console::WriteLine("The field is assigned the integer value: {0}",
            myIntObj->myField);

   double myDouble = 0.123;
   MyGenStruct<double>^ myDoubleObj = gcnew MyGenStruct<double>();
   myDoubleObj->AssignValue(myDouble);
   Console::WriteLine("The field is assigned the double value: {0}",
            myDoubleObj->myField);

   String^ myString = "Hello Generics!";
   MyGenStruct<String^>^ myStringObj = gcnew MyGenStruct<String^>();
   myStringObj->AssignValue(myString);
   Console::WriteLine("The field is assigned the string: {0}",
            myStringObj->myField);
}
```

```Output
The field is assigned the integer value: 123
The field is assigned the double value: 0.123
The field is assigned the string: Hello Generics!
```

## <a name="see-also"></a>另請參閱

[泛型](generics-cpp-component-extensions.md)
