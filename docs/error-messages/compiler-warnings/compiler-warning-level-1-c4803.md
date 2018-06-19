---
title: 編譯器警告 （層級 1） C4803 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4803
dev_langs:
- C++
helpviewer_keywords:
- C4803
ms.assetid: 2552f3a6-c418-49f4-98a2-a929857be658
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c574b51fc13f9224d48495f8b591a56abdc74966
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33280825"
---
# <a name="compiler-warning-level-1-c4803"></a>編譯器警告 (層級 1) C4803
'method': 產生的方法具有不同的儲存類別不同的事件 'event'  
  
事件方法必須有相同的儲存類別和事件宣告。 編譯器會調整事件的方法，讓儲存體類別都相同。  
  
如果您擁有實作事件介面的類別，會發生這個警告。 編譯器不會隱含地產生介面中的事件引發方法。 當您在類別中實作該介面時，編譯器並隱含地產生引發方法，該方法不是虛擬的因此警告。 如需事件的詳細資訊，請參閱[事件](../../windows/event-cpp-component-extensions.md)。  
  
請參閱[警告](../../preprocessor/warning.md)pragma，如需有關如何關閉警告資訊。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4803。  
  
```  
// C4803.cpp  
// compile with: /clr /W1  
using namespace System;  
  
public delegate void Del();  
  
ref struct E {  
   Del ^ _pd1;  
   event Del ^ E1 {  
      void add (Del ^ pd1) {  
         _pd1 = dynamic_cast<Del ^>(Delegate::Combine(_pd1, pd1));  
      }  
  
      void remove(Del^ pd1) {  
         _pd1 = dynamic_cast<Del^> (Delegate::Remove(_pd1, pd1));  
      }  
  
      virtual void raise() {   // C4803 warning (remove virtual)  
         if (_pd1)  
            _pd1();  
      }  
   }  
  
   void func() {  
      Console::WriteLine("In E::func()");  
   }  
};  
  
int main() {  
   E ^ ep = gcnew E;  
   ep->E1 += gcnew Del(ep, &E::func);  
   ep->E1();  
   ep->E1 -= gcnew Del(ep, &E::func);  
   ep->E1();  
}  
```  
