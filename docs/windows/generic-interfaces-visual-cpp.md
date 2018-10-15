---
title: 泛型介面 (C + + /cli CLI) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- generic interfaces
- interfaces, generic [C++}
ms.assetid: f3da788a-ba83-4db7-9dcf-9b95a8fb9d1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e36a4c1d9604753fd4bff6a51df060e1d26822fb
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328359"
---
# <a name="generic-interfaces-ccli"></a>泛型介面 (C + + /cli CLI)

套用至型別參數，在類別上的限制會套用至型別參數，在介面上的相同 (請參閱[泛型類別 (C + + /cli CLI)](../windows/generic-classes-cpp-cli.md))。

控制函式多載的規則也適用於泛型類別或泛型介面中的函式。

明確介面成員實作會使用相同的方式為使用簡單的介面型別 （請參閱下列範例） 中的建構的介面類型。

如需有關介面的詳細資訊，請參閱 <<c0> [ 介面類別](../windows/interface-class-cpp-component-extensions.md)。

## <a name="syntax"></a>語法

```cpp
[attributes] generic <class-key type-parameter-identifier[, ...]>
[type-parameter-constraints-clauses][accesibility-modifiers] interface class identifier [: base-list] {   interface-body} [declarators] ;
```

## <a name="remarks"></a>備註

*屬性*<br/>
（選擇性）其他宣告資訊。 如需有關屬性和屬性類別的詳細資訊，請參閱**屬性**。

*類別索引鍵*<br/>
**類別**或**typename**

*type-parameter-identifier(s)*<br/>
以逗號分隔的識別碼清單。

*類型參數條件約束-子句*<br/>
中指定的格式[泛型類型參數的條件約束 (C + + /cli CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md)

*存取範圍修飾詞*<br/>
（選擇性）存取範圍修飾詞 (例如**公用、 私用**)。

*identifier*<br/>
介面名稱。

*基底清單*<br/>
（選擇性）包含一或多個明確的基底介面並以逗號分隔的清單。

*介面主體內*<br/>
介面成員的宣告。

*宣告子*<br/>
（選擇性）根據此類型的變數的宣告。

## <a name="example"></a>範例

下列範例示範如何宣告和具現化泛型介面。 在範例中，泛型介面`IList<ItemType>`宣告。 兩個泛型類別，然後實作`List1<ItemType>`和`List2<ItemType>`，使用不同的實作。

```cpp
// generic_interface.cpp
// compile with: /clr
using namespace System;

// An exception to be thrown by the List when
// attempting to access elements beyond the
// end of the list.
ref class ElementNotFoundException : Exception {};

// A generic List interface
generic <typename ItemType>
public interface class IList {
   ItemType MoveFirst();
   bool Add(ItemType item);
   bool AtEnd();
   ItemType Current();
   void MoveNext();
};

// A linked list implementation of IList
generic <typename ItemType>
public ref class List1 : public IList<ItemType> {
   ref class Node {
      ItemType m_item;

   public:
      ItemType get_Item() { return m_item; };
      void set_Item(ItemType value) { m_item = value; };

      Node^ next;

      Node(ItemType item) {
         m_item = item;
         next = nullptr;
      }
   };

   Node^ first;
   Node^ last;
   Node^ current;

   public:
   List1() {
      first = nullptr;
      last = first;
      current = first;
   }

   virtual ItemType MoveFirst() {
      current = first;
      if (first != nullptr)  
        return first->get_Item();
      else
         return ItemType();
   }

   virtual bool Add(ItemType item) {
      if (last != nullptr) {
         last->next = gcnew Node(item);
         last = last->next;
      }
      else {
         first = gcnew Node(item);
         last = first;
         current = first;
      }
      return true;
   }

   virtual bool AtEnd() {
      if (current == nullptr )  
        return true;
      else
        return false;
   }

   virtual ItemType Current() {
       if (current != nullptr)  
         return current->get_Item();
       else
         throw gcnew ElementNotFoundException();
   }

   virtual void MoveNext() {
      if (current != nullptr)  
       current = current->next;
      else
        throw gcnew ElementNotFoundException();
   }
};

// An array implementation of IList
generic <typename ItemType>
ref class List2 : public IList<ItemType> {
   array<ItemType>^ item_array;
   int count;
   int current;

   public:

   List2() {
      // not yet possible to declare an
      // array of a generic type parameter
      item_array = gcnew array<ItemType>(256);
      count = current = 0;
   }

   virtual ItemType MoveFirst() {
      current = 0;
      return item_array[0];
   }

   virtual bool Add(ItemType item) {
      if (count < 256)  
         item_array[count++] = item;
      else
        return false;
      return true;
   }

   virtual bool AtEnd() {
      if (current >= count)  
        return true;
      else
        return false;
   }

   virtual ItemType Current() {
      if (current < count)  
        return item_array[current];
      else
        throw gcnew ElementNotFoundException();
   }

   virtual void MoveNext() {
      if (current < count)  
         ++current;
      else
         throw gcnew ElementNotFoundException();
   }
};

// Add elements to the list and display them.
generic <typename ItemType>
void AddStringsAndDisplay(IList<ItemType>^ list, ItemType item1, ItemType item2) {
   list->Add(item1);
   list->Add(item2);
   for (list->MoveFirst(); ! list->AtEnd(); list->MoveNext())  
   Console::WriteLine(list->Current());
}

int main() {
   // Instantiate both types of list.

   List1<String^>^ list1 = gcnew List1<String^>();
   List2<String^>^ list2 = gcnew List2<String^>();

   // Use the linked list implementation of IList.
   AddStringsAndDisplay<String^>(list1, "Linked List", "List1");

   // Use the array implementation of the IList.
   AddStringsAndDisplay<String^>(list2, "Array List", "List2");
}
```

```Output
Linked List
List1
Array List
List2
```

## <a name="example"></a>範例

這個範例會宣告泛型介面， `IMyGenIface`，和兩個非泛型介面，`IMySpecializedInt`並`ImySpecializedString`，，特製化`IMyGenIface`。 兩個特製化的介面則由兩個類別，實作`MyIntClass`和`MyStringClass`。 此範例示範如何特製化的泛型介面具現化泛型和非泛型介面，介面上呼叫的明確實作的成員。

```cpp
// generic_interface2.cpp
// compile with: /clr
// Specializing and implementing generic interfaces.
using namespace System;

generic <class ItemType>
public interface class IMyGenIface {
   void Initialize(ItemType f);
};

public interface class IMySpecializedInt: public IMyGenIface<int> {
   void Display();
};

public interface class IMySpecializedString: public IMyGenIface<String^> {
   void Display();
};

public ref class MyIntClass: public IMySpecializedInt {
   int myField;

public:
   virtual void Initialize(int f) {
      myField = f;
   }

   virtual void Display() {
      Console::WriteLine("The integer field contains: {0}", myField);
   } 
};

public ref struct MyStringClass: IMySpecializedString { 
   String^ myField;

public:
   virtual void Initialize(String^ f) {
      myField = f;
    }

   virtual void Display() {
      Console::WriteLine("The String field contains: {0}", myField);
   }
};

int main() {
   // Instantiate the generic interface.
   IMyGenIface<int>^ myIntObj = gcnew MyIntClass();

   // Instantiate the specialized interface "IMySpecializedInt."
   IMySpecializedInt^ mySpIntObj = (IMySpecializedInt^) myIntObj;

   // Instantiate the generic interface.
   IMyGenIface<String^>^ myStringObj = gcnew MyStringClass();

   // Instantiate the specialized interface "IMySpecializedString."
   IMySpecializedString^ mySpStringObj =
            (IMySpecializedString^) myStringObj;

   // Call the explicitly implemented interface members.
   myIntObj->Initialize(1234);
   mySpIntObj->Display();

   myStringObj->Initialize("My string");
   mySpStringObj->Display();
}
```

```Output
The integer field contains: 1234
The String field contains: My string
```

## <a name="see-also"></a>另請參閱

[泛型](../windows/generics-cpp-component-extensions.md)