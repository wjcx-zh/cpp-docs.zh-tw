---
title: 使用泛型 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], consuming from .NET languages
ms.assetid: e6330ef5-e907-432e-b527-7a22f5899639
ms.openlocfilehash: bea22a0d9fdc5c1ddbd9da2af7078228a6315e80
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414135"
---
# <a name="consuming-generics-ccli"></a>使用泛型 (C++/CLI)

以某一種 .NET (或 UWP) 語言撰寫的泛型可以在其他語言中使用。 與範本不同的是，泛型在編譯的組件中仍然保持為泛型。 因此，您可以在不同組件中，甚至以與定義泛型類型的組件不同的語言，將泛型類型具現化。

## <a name="example-generic-class-defined-in-c"></a>範例：在 C 中定義的泛型類別#

### <a name="description"></a>描述

這個範例將示範以 C# 定義的泛型類別。

### <a name="code"></a>程式碼

```csharp
// consuming_generics_from_other_NET_languages.cs
// compile with: /target:library
// a C# program
public class CircularList<ItemType> {
   class ListNode    {
      public ItemType m_item;
      public ListNode next;
      public ListNode(ItemType item) {
         m_item = item;
      }
   }

   ListNode first, last;

   public CircularList() {}

   public void Add(ItemType item) {
      ListNode newnode = new ListNode(item);
      if (first == null) {
         first = last = newnode;
         first.next = newnode;
         last.next = first;
      }
      else {
         newnode.next = first;
         first = newnode;
         last.next = first;
      }
   }

   public void Remove(ItemType item) {
      ListNode iter = first;
      if (first.m_item.Equals( item )) {
         first =
         last.next = first.next;
      }
      for ( ; iter != last ; iter = iter.next )
         if (iter.next.m_item.Equals( item )) {
              if (iter.next == last)
                  last = iter;
              iter.next = iter.next.next;
              return;
          }
   }

   public void PrintAll() {
      ListNode iter = first;
      do {
         System.Console.WriteLine( iter.m_item );
         iter = iter.next;
      } while (iter != last);
   }
}
```

## <a name="example-consume-assembly-authored-in-c"></a>範例：使用以 C 撰寫的元件#

### <a name="description"></a>描述

這個範例會使用以 C# 撰寫的組件。

### <a name="code"></a>程式碼

```cpp
// consuming_generics_from_other_NET_languages_2.cpp
// compile with: /clr
#using <consuming_generics_from_other_NET_languages.dll>
using namespace System;
class NativeClass {};
ref class MgdClass {};

int main() {
   CircularList<int>^ circ1 = gcnew CircularList<int>();
   CircularList<MgdClass^>^ circ2 = gcnew CircularList<MgdClass^>();

   for (int i = 0 ; i < 100 ; i += 10)
      circ1->Add(i);
   circ1->Remove(50);
   circ1->PrintAll();
}
```

```Output
90
80
70
60
40
30
20
10
```

## <a name="see-also"></a>另請參閱

[泛型](generics-cpp-component-extensions.md)
