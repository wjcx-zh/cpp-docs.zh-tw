---
title: 如何： 針對每個反覆查看泛型集合與 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- generic collection, iterating over
ms.assetid: 00288d53-3d41-44d0-be5b-b3033456ceaa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: aab17b54f27887672386575a20808a0799a9d12d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438206"
---
# <a name="how-to-iterate-over-a-generic-collection-with-for-each"></a>如何：使用 for each 反覆查看泛型集合

[泛型](../windows/generics-cpp-component-extensions.md)Visual c + + 的功能可讓您建立泛型集合。

## <a name="example"></a>範例

此範例示範如何將 `for each` 用於簡單泛型值類型集合。

```
// for_each_generics.cpp
// compile with: /clr
using namespace System;
using namespace System::Collections::Generic;

generic <class T>
public value struct MyArray : public IEnumerable<T> {

   MyArray( array<T>^ d ) {
      data = d;
   }

   ref struct enumerator : IEnumerator<T> {
      enumerator( MyArray^ myArr ) {
         colInst = myArr;
         currentIndex = -1;
      }

      virtual bool MoveNext() = IEnumerator<T>::MoveNext {
         if ( currentIndex < colInst->data->Length - 1 ) {
            currentIndex++;
            return true;
         }

         return false;
      }

      virtual property T Current {
         T get() {
            return colInst->data[currentIndex];
         }
      };

      property Object^ CurrentNonGeneric {
         virtual Object^ get() = System::Collections::IEnumerator::Current::get {
            return colInst->data[currentIndex];
         }
      };

      virtual void Reset() {}
      ~enumerator() {}

      MyArray^ colInst;
      int currentIndex;
   };

   array<T>^ data;

   virtual IEnumerator<T>^ GetEnumerator() {
      return gcnew enumerator(*this);
   }
   virtual System::Collections::IEnumerator^ GetEnumeratorNonGeneric() = System::Collections::IEnumerable::GetEnumerator {
      return gcnew enumerator(*this);
   }
};

int main() {
   MyArray<int> col = MyArray<int>( gcnew array<int>{10, 20, 30 } );

   for each ( Object^ c in col )
      Console::WriteLine((int)c);
}
```

```Output
10
20
30
```

## <a name="see-also"></a>另請參閱

[for each, in](../dotnet/for-each-in.md)