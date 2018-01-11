---
title: "泛型類別 (C + + /CLI) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- classes [C++], generic
- generic classes [C++], about generic classes
- data types [C++], generic
- generic classes
- generics [C++], declaring generic classes
ms.assetid: 0beb99e1-1ec4-4fee-9836-ce9657d67a3a
caps.latest.revision: "33"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 22f2d00c4f8e07ea9d04e03c2e95190be056cbd9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="generic-classes-ccli"></a>泛型類別 (C++/CLI)
泛型類別宣告使用下列格式：  
  
## <a name="syntax"></a>語法  
  
```  
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
 在上述語法中，使用下列詞彙：  
  
 `attributes` (選擇性)  
 其他宣告資訊。 如需關於屬性及屬性類別的詳細資訊，請參閱＜屬性＞。  
  
 *類別索引鍵*  
 可能是`class`或`typename`  
  
 *類型為參數的識別項*，  
 以逗號分隔清單的指定名稱的型別參數的識別項。  
  
 *條件約束子句*  
 （不以逗號分隔） 的清單**其中**子句指定的型別參數條件約束。 採用下列格式：  
  
 `where`  *型別參數識別碼*`:`*條件約束清單*   `...`  
  
 *條件約束清單*  
 *類別或介面*[`,` *...*]  
  
 *存取範圍修飾詞*  
 泛型類別存取範圍修飾詞。 為 Windows 執行階段中，唯一允許的修飾詞是`private`。 允許的修飾詞的 common language runtime`private`和`public`。  
  
 *identifier*  
 泛型類別，也就是任何有效的 c + + 識別項名稱。  
  
 *修飾詞*（選擇性）  
 允許修飾詞包含`sealed`和**抽象**。  
  
 *基底清單*  
 清單，其中包含一個基底類別，以及任何實作介面，以逗號分隔。  
  
 *在類別主體*  
 類別包含的欄位、 成員函式等的內文。  
  
 *宣告子*  
 此類型的任何變數的宣告。 例如： `^`*識別碼*[`,` ...]  
  
 您可以宣告泛型類別，這類 (請注意，關鍵字**類別**可能而不是使用**typename**)。 在此範例中， `ItemType`，`KeyType`和`ValueType`是未知的型別指定點的位置類型。 `HashTable<int, int>`為建構的類型的泛型型別`HashTable<KeyType, ValueType>`。 可以從單一泛型類型建構不同結構類型的數目。 建構自泛型類別的建構的類型會視為任何其他 ref 類別類型。  
  
```  
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
  
 同時實值類型 (其中一個內建類型，例如`int`或`double`，或使用者定義的實值類型) 和參考型別可能會用做為泛型型別引數。 泛型定義中的語法是相同而定。 在語法上，如同它是參考型別，被視為未知的類型。 不過，執行階段就能判斷實際使用的型別是否為實值類型，並以取代適當產生的程式碼直接成員的存取權。 實值類型做為泛型型別引數不會進行 boxed 處理，因此不會發生 boxing 相關聯的效能負面影響。 泛型主體內使用的語法應該是**T ^**和 '**->**' 而不是 '**。**'。 使用的任何[ref 新 gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)類型參數會適當地解譯由執行階段為實值類型的簡單建立如果型別引數是實值類型。  
  
 您也可以宣告泛型類別與[泛型型別參數的條件約束 (C + + CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md)上可以使用的型別參數的型別。 在下列範例中任何類型用於`ItemType`必須實作`IItem`介面。 嘗試使用`int`，比方說，這不會實作`IItem`，會產生編譯時間錯誤，因為型別引數未滿足的條件約束。  
  
```  
// generic_classes_2.cpp  
// compile with: /clr /c  
interface class IItem {};  
generic <class ItemType>  
where ItemType : IItem  
ref class Stack {};  
```  
  
 無法多載相同的命名空間中的泛型類別，藉由只變更數或型別參數的型別。 不過，如果每個類別位於不同的命名空間，但可以在多載。 例如，請考慮下列兩個類別：`MyClass`和`MyClass<ItemType>`，命名空間中`A`和`B`。 兩個類別可以再多載中的第三個命名空間為 c:  
  
```  
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
  
 基底類別和基底介面不能是型別參數。 然而，基底類別可以包含型別參數做為引數，如下列範例所示：  
  
```  
// generic_classes_4.cpp  
// compile with: /clr /c  
generic <typename ItemType>  
interface class IInterface {};  
  
generic <typename ItemType>  
ref class MyClass : IInterface<ItemType> {};  
```  
  
 建構函式和解構函式會執行一次針對每個物件執行個體 （如往常般）;靜態建構函式會執行一次，每個建構的類型。  
  
## <a name="fields-in-generic-classes"></a>泛型類別中的欄位  
 本節示範如何使用執行個體和泛型類別中的靜態欄位。  
  
### <a name="instance-variables"></a>執行個體變數  
 泛型類別的執行個體變數可以有型別和包含任何從封入類別的型別參數的變數初始設定式。  
  
## <a name="example"></a>範例  
 在下列範例中，三個不同的執行個體的泛型類別為 MyClass\<ItemType >，會建立使用適當的型別引數 (`int`， **double**，和**字串**).  
  
```  
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
 建立新的泛型型別時，會建立任何靜態變數的新執行個體，該型別的任何靜態建構函式會執行。  
  
 靜態變數可以使用從封入類別的任何型別參數。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用靜態欄位和泛型類別內的靜態建構函式。  
  
```  
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
 泛型類別中的方法可以是泛型本身;非泛型方法會由類別型別參數隱含參數化。  
  
 下列的特殊規則套用至泛型類別內的方法：  
  
-   泛型類別中的方法可以當做參數、 傳回型別或本機變數的型別參數。  
  
-   泛型類別中的方法可以當做參數、 傳回型別或本機變數使用開放式或封閉式的建構的類型。  
  
### <a name="non-generic-methods-in-generic-classes"></a>泛型類別中的非泛型方法  
 沒有任何其他型別參數的泛型類別中的方法通常稱為非泛型雖然它們隱含參數化的封入泛型類別。  
  
 非泛型方法的簽章可以包含一或多個封入類別的型別參數，直接或開放式建構類型。 例如:   
  
 `void MyMethod(MyClass<ItemType> x) {}`  
  
 這類方法的主體，也可以使用這些型別參數。  
  
## <a name="example"></a>範例  
 下列範例會宣告非泛型方法， `ProtectData`，在泛型類別， `MyClass<ItemType>`。 此方法會使用類別型別參數`ItemType`開放式建構類型在其簽章中。  
  
```  
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
 您可以宣告泛型和非泛型類別中的泛型方法。 例如:   
  
## <a name="example"></a>範例  
  
```  
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
  
 非泛型方法仍為泛型，因為它由類別的型別參數，參數化，但它有沒有其他的型別參數。  
  
 所有類型的泛型類別中的方法可以都是泛型，包括靜態、 執行個體和虛擬方法。  
  
## <a name="example"></a>範例  
 下列範例會示範宣告和使用泛型類別內的泛型方法：  
  
```  
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
  
## <a name="using-nested-types-in-generic-classes"></a>泛型類別中使用巢狀的類型  
 就像一般類別中，您可以宣告泛型類別內的其他類型。 巢狀的類別宣告隱含外部類別宣告的型別參數所參數化。 因此，每個建構外部型別定義不同的巢狀的類別。 例如，在宣告中，  
  
```  
// generic_classes_5.cpp  
// compile with: /clr /c  
generic <typename ItemType>  
ref struct Outer {  
   ref class Inner {};  
};  
```  
  
 類型為 Outer\<int >:: 內部不是外部的類型相同\<雙 >:: 內部。  
  
 如同在泛型類別中的泛型方法，可以定義其他的型別參數的巢狀類型。 如果您使用相同的型別參數名稱，內部和外部類別中，內部型別參數就會隱藏外部型別參數。  
  
```  
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
  
 因為沒有任何方法可以參考外部型別參數，編譯器會產生警告，以在此情況下。  
  
 當命名巢狀建構的泛型類型時，外部型別之型別參數不在型別參數清單，做為內部的類型，即使隱含外部型別的型別參數所參數化內部型別。 在上述情況中，建構類型的名稱就是外部\<int >:: 內部\<字串 >。  
  
 下列範例示範如何建立和讀取在泛型類別中使用巢狀的類型的連結的清單。  
  
## <a name="example"></a>範例  
  
```  
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
  
## <a name="properties-events-indexers-and-operators-in-generic-classes"></a>屬性、 事件、 索引子和泛型類別中的運算子  
  
-   屬性、 事件、 索引子和運算子可以使用封入泛型類別的型別參數做為傳回值、 參數或區域變數，例如當`ItemType`是類別的型別參數：  
  
    ```  
    public ItemType MyProperty {}  
    ```  
  
-   屬性、 事件、 索引子和運算子不能自行進行參數化。  
  
## <a name="example"></a>範例  
 此範例顯示泛型類別內的執行個體屬性的宣告。  
  
```  
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
 下一個範例顯示泛型類別與事件。  
  
```  
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
 宣告和使用泛型結構的規則是一樣的泛型類別，除了在 Visual c + + 語言參考中所述的差異之外。  
  
## <a name="example"></a>範例  
 下列範例會宣告為泛型結構， `MyGenStruct`，具有一個欄位， `myField`，並指派不同類型的值 (`int`， **double**，**字串 ^**) 為此欄位。  
  
```  
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
  
## <a name="see-also"></a>請參閱  
 [泛型](../windows/generics-cpp-component-extensions.md)