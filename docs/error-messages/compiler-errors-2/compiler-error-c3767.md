---
title: 編譯器錯誤 C3767
ms.date: 11/04/2016
f1_keywords:
- C3767
helpviewer_keywords:
- C3767
ms.assetid: 5247cdcd-639c-4527-bd37-37e74c4e8fab
ms.openlocfilehash: 61f7479986cccfa3851d85bf8e7bc0e9da3d1cea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400197"
---
# <a name="compiler-error-c3767"></a>編譯器錯誤 C3767

無法存取的 'function' 候選函式

在類別中定義 friend 函式不應視為如同它已定義，並在全域命名空間範圍中宣告。 可以不過，引數相依查閱找到。

一項重大變更可能也會造成 C3767： 原生類型現在是預設會在私用 **/clr**編譯; 請參閱[輸入可視性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)如需詳細資訊。

## <a name="example"></a>範例

下列範例會產生 C3767:

```
// C3767a.cpp
// compile with: /clr
using namespace System;
public delegate void TestDel();

public ref class MyClass {
public:
   static event TestDel^ MyClass_Event;
};

public ref class MyClass2 : public MyClass {
public:
   void Test() {
      MyClass^ patient = gcnew MyClass;
      patient->MyClass_Event();
    }
};

int main() {
   MyClass^ x = gcnew MyClass;
   x->MyClass_Event();   // C3767

   // OK
   MyClass2^ y = gcnew MyClass2();
   y->Test();
};
```

下列範例會產生 C3767:

```
// C3767c.cpp
// compile with: /clr /c

ref class Base  {
protected:
   void Method() {
      System::Console::WriteLine("protected");
   }
};

ref class Der : public Base {
   void Method() {
      ((Base^)this)->Method();   // C3767
      // try the following line instead
      // Base::Method();
   }
};
```

