---
title: "Generic Classes (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "classes [C++], generic"
  - "generic classes [C++], about generic classes"
  - "data types [C++], generic"
  - "generic classes"
  - "generics [C++], declaring generic classes"
ms.assetid: 0beb99e1-1ec4-4fee-9836-ce9657d67a3a
caps.latest.revision: 33
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Generic Classes (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

泛型類別會使用下列形式宣告：  
  
## 語法  
  
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
  
## 備註  
 上列語法中，會使用下列術語。  
  
 `attributes` \(選擇性\)  
 補充宣告資訊。  如需關於屬性及屬性類別的詳細資訊，請參閱屬性。  
  
 *class\-key*  
 `class` 或 `typename`。  
  
 *type\-parameter\-identifier\(s\)*,  
 以逗點分隔的識別碼清單指定型別參數的名稱。  
  
 *constraint\-clauses*  
 **where** 子句的清單\(非逗點分隔\)指定型別參數的限制。  採用格式：  
  
 `where`  *type\-parameter\-identifier*  `:`  *constraint\-list*  `...`  
  
 *constraint\-list*  
 *class\-or\-interface*\[`,` *...*\]  
  
 *accessibility\-modifiers*  
 泛型類別的可視性修飾語  對於 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]，唯一允許的修飾語為 `private`。  對於 common language runtime，允許的修飾語為 `private` 和 `public`。  
  
 *identifier*  
 泛型類別的名稱，任何有效的 C\+\+ 識別碼。  
  
 *修飾詞*\(選擇性\)  
 允許的修飾詞包含`sealed` 和 **abstract**。  
  
 *base\-list*  
 包含一個基底類別及任和實作介面的清單，皆以逗點分隔。  
  
 *class\-body*  
 類別的主體，包含域、成員函式等等。  
  
 *宣告子*  
 這個型別的任何變數的宣告。  例如： `^`*識別項* \[`,` …\]  
  
 您可以宣告如這些的泛型類別 \(請注意可能使用關鍵字 **class** 而非 **typename**\)。  在此範例中， `ItemType`、 `KeyType` 和 `ValueType` 所指定的屬性型別的型別不明。  `HashTable<int, int>` 是泛型型別 `HashTable<KeyType, ValueType>`的建構型別。  許多不同的建構型別可以從單一泛型型別建構。  從泛型類別建構的建構型別被視為其他的 ref 類別型別。  
  
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
  
 實值型別 \(或內建型別例如 `int` 或 `double`或使用者定義的實值型別\) 和參考型別皆可做為泛型型別引數。  在泛型定義中的語法無論如何都是相同的。  在語句構造上，未知的型別會像參考型別般被看待。  不過，執行階段可以決定，如果實際使用的型別是實值型別 \(Value Type\) 且對直接存取成員替代適當產生的程式碼。  做為泛型型別引數的實值型別沒有 boxed，因此不會損失與 Boxing 相關的效能。  在泛型主體中使用的語法應該是 **T^** 和 '**\-\>**' 而非 '**.**'。  如果型別引數是實值型別，對型別參數之 [ref new, gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md) 的使用要在執行階段正確解譯為實值型別的簡單建立。  
  
 您也可以使用可作為型別參數的型別之 [Constraints on Generic Type Parameters \(C\+\+\/CLI\)](../windows/constraints-on-generic-type-parameters-cpp-cli.md) 來宣告泛型類別。  在下列範例中用於 `ItemType` 的任何型別都必須實作 `IItem` 介面。  嘗試使用 `int`，例如，不實作 `IItem`，將會導致編譯時期錯誤，因為型別引數未滿足條件約束。  
  
```  
// generic_classes_2.cpp  
// compile with: /clr /c  
interface class IItem {};  
generic <class ItemType>  
where ItemType : IItem  
ref class Stack {};  
```  
  
 在相同命名空間的泛型類別不可以只變更數字或型別參數的型別多載。  不過，如果每個類別位在不同的命名空間，它們可以多載。  例如，請考量下列兩個類別， `MyClass` 與 `MyClass<ItemType>`，在命名空間 `A` 和 `B` 中。  兩個類別在第三個命名空間 C\# 可以多載：  
  
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
  
 基底類別和基底介面無法為型別參數。  不過，基底類別可以包含型別參數做為引數，如下列情形：  
  
```  
// generic_classes_4.cpp  
// compile with: /clr /c  
generic <typename ItemType>  
interface class IInterface {};  
  
generic <typename ItemType>  
ref class MyClass : IInterface<ItemType> {};  
```  
  
 建構函式和解構函式為每個執行個體一次執行 \(照常\)：靜態建構函式為每個建構型別執行一次。  
  
## 泛型類別的欄位。  
 本節示範泛型類別的執行個體和靜態欄位。  
  
### 執行個體變數。  
 泛型類別的執行個體變數可能會包含從封入類別的任何型別參數的型別和變數初始設定式。  
  
## 範例  
 在下列範例中，泛型類別 MyClass\<ItemType\> 的三個不同的執行個體由使用適合的型別引數\(`int`、 **double** 和 **string**\)所建立。  
  
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
  
  **Integer field \= 123**  
**Double field \= 1.23**  
**String field \= ABC**   
## 靜態變數。  
 在泛型型別的建立，任何靜態變數的新執行個體被建立且任何該型別的靜態建構函式被執行。  
  
 靜態變數可以從封入類別中使用任何型別參數。  
  
## 範例  
 下列範例示範在泛型類別內使用靜態欄位和靜態建構函式。  
  
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
  
  **Static constructor called.**  
**Static constructor called.**  
**Static constructor called.**  
**Test1**   
## 在泛型類別的方法  
 在泛型類別的方法可以是泛型自己：非泛型方法會由類別型別參數的隱含參數化。  
  
 下列特殊規則套用至泛型類別內的方法：  
  
-   在泛型類別的方法可以使用型別參數做為參數、傳回型別或區域變數。  
  
-   在泛型類別的方法可以使用開放式或封閉式建構型別做為參數、傳回型別或區域變數。  
  
### 在泛型類別的非泛型方法  
 在沒有其他型別參數的泛型類別的方法通常是指非泛型，但這些由封入泛型類別隱含參數化。  
  
 非泛型方法的簽章可能包含一或多個封入類別的型別參數，直接或以開放式建構型別。  例如：  
  
 `void MyMethod(MyClass<ItemType> x) {}`  
  
 這類方法的主體也可以使用這些型別參數。  
  
## 範例  
 下列範例會宣告非泛型方法`ProtectData`，在泛型類別內，則為 `MyClass<ItemType>`。  此方法使用在開放式建構型別的簽章之類別型別參數 `ItemType` 。  
  
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
  
  **Name: Jeff Smith**  
**Amount: $123.00\*\***   
## 在泛型類別的泛型方法  
 您可以在泛型和非泛型類別中宣告泛型方法。  例如：  
  
## 範例  
  
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
  
 非泛型方法依然是泛型，因為它會由類別的型別參數不同，不過它不具有不同的型別參數。  
  
 泛型類別中方法的所有型別可以是泛型，包括靜態、執行個體和虛擬方法。  
  
## 範例  
 下列範例示範如何宣告和使用泛型類別的泛型方法：  
  
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
  
  **MyMethod returned: 12**  
**MyMethod returned: Hello \#1**  
**MyMethod returned: Hello World\!**   
## 使用泛型類別的巢狀型別  
 如同原本的類別，您可以在泛型類別內宣告其他型別。  巢狀類別宣告由外部類別宣告的型別參數的隱含參數化。  因此，不同的巢狀類別為每個建構的外部型別定義。  例如，在宣告中，  
  
```  
// generic_classes_5.cpp  
// compile with: /clr /c  
generic <typename ItemType>  
ref struct Outer {  
   ref class Inner {};  
};  
```  
  
 這個型別 Outer\<int\>::Inner 與型別 Outer\<double\>::Inner 不同。  
  
 在泛型類別的泛型方法，其他型別參數可以為巢狀型別定義。  如果您在內部和外部類別使用相同型別參數名稱，這個內部型別參數會隱藏這個外部型別參數。  
  
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
  
 在這種情況下因為無法參考外部型別參數，編譯器將會產生警告。  
  
 當建構的巢狀泛型型別被命名時，這個外部型別的型別參數在這個內建型別的型別參數清單中未包含，即使這個內部型別由外部型別的型別參數的隱含參數化。  上述情況，建構型別的名稱將會是 Outer\<int\>::Inner\<string\>。  
  
 下列範例示範如何使用泛型類別的巢狀型別建置和讀取連結清單。  
  
## 範例  
  
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
  
  **Building the list:**  
**0.1**  
**0.2**  
**0.3**  
**0.4**  
**0.5**  
**Reading nodes:**  
**0.5**  
**0.4**  
**0.3**  
**0.2**  
**0.1**   
## 泛型中的屬性、事件、索引子和運算子  
  
-   屬性、事件、索引子和運算子可以使用封入泛型類別的型別參數做為傳回值、參數或區域變數，例如在 `ItemType` 是類別的型別參數時：  
  
    ```  
    public ItemType MyProperty {}  
    ```  
  
-   屬性、事件、索引子、運算子無法自己參數化。  
  
## 範例  
 這個範例會顯示一個執行個體的屬性宣告在泛型類別中。  
  
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
  
  **John, 234**   
## 範例  
 下一個範例會顯示具有事件的泛型類別。  
  
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
  
## 泛型結構  
 宣告和使用泛型結構的規則與泛型類別的相同，除了在 Visual C\+\+ 語言參考中記錄的那些不同。  
  
## 範例  
 下列範例宣告泛型結構，`MyGenStruct`，具有一個欄位則為 `myField`，並指派不同的型別 \(`int`、**double**、**String^**\) 的值給欄位。  
  
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
  
  **The field is assigned the integer value: 123**  
**The field is assigned the double value: 0.123**  
**The field is assigned the string: Hello Generics\!**   
## 請參閱  
 [Generics](../windows/generics-cpp-component-extensions.md)