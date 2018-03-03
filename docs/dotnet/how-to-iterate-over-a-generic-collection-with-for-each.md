---
title: "如何： 反覆查看泛型集合的每個 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- generic collection, iterating over
ms.assetid: 00288d53-3d41-44d0-be5b-b3033456ceaa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ed9d92c4d6123d1c9c8f92814272ae5a77184102
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>請參閱  
 [for each, in](../dotnet/for-each-in.md)