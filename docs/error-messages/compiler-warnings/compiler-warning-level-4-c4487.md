---
title: 編譯器警告 （層級 4） C4487 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4487
dev_langs:
- C++
helpviewer_keywords:
- C4487
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80008dbcfbebe4e91398e651e361efe7df30b641
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4487"></a>編譯器警告 (層級 4) C4487
'derived_class_function': 符合繼承的非虛擬方法 'base_class_function'，但未明確標記為 'new'  
  
 在衍生類別中的函式有相同的簽章的非虛擬基底類別函式。 C4487 提醒您在衍生的類別函式不覆寫基底類別函式。 將衍生的類別函式明確標示`new`若要解決這個警告。  
  
 如需詳細資訊，請參閱[新 (新 vtable 中的位置）](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4487。  
  
```  
// C4487.cpp  
// compile with: /W4 /clr  
using namespace System;  
public ref struct B {  
   void f() { Console::WriteLine("in B::f"); }  
   void g() { Console::WriteLine("in B::g"); }  
};  
  
public ref struct D : B {  
   void f() { Console::WriteLine("in D::f"); }   // C4487  
   void g() new { Console::WriteLine("in D::g"); }   // OK  
};  
  
int main() {  
   B ^ a = gcnew D;  
   // will call base class functions  
   a->f();  
   a->g();  
}  
```