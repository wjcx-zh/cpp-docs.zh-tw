---
title: 編譯器錯誤 C3918
ms.date: 11/04/2016
f1_keywords:
- C3918
helpviewer_keywords:
- C3918
ms.assetid: a8b3a90a-3fe1-4244-a5ff-a31cdae97d98
ms.openlocfilehash: ff2b59338c707767fa1d3c382feaa1bfcdf29ce2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758485"
---
# <a name="compiler-error-c3918"></a>編譯器錯誤 C3918

使用方式要求 ' member ' 必須是資料成員

C3918 可能發生的原因有數種與事件相關。

## <a name="example"></a>範例

C3918 可能發生，因為目前的內容中需要類別成員。 下列範例會產生 C3918。

```cpp
// C3918.cpp
// compile with: /clr /c
public ref class C {
public:
   System::Object ^ o;
   delegate void Del();

   event Del^ MyEvent {
      void add(Del^ev) {
         if ( MyEvent != nullptr) {}   // C3918
         if ( o != nullptr) {}   // OK
   }
   void remove(Del^){}
   }
};
```

## <a name="example"></a>範例

如果您嘗試檢查 null 的簡單事件（事件名稱將不再提供事件的備份存放區委派的直接存取權），也會導致 C3918。

下列範例會產生 C3918。

```cpp
// C3918_2.cpp
// compile with: /clr /c
using namespace System;
public delegate int MyDel(int);

interface struct IEFace {
   event MyDel ^ E;
};

ref struct EventSource : public IEFace {
   virtual event MyDel ^ E;
   void Fire_E(int i) {
      if (E)   // C3918
         E(i);
   }
};
```

## <a name="example"></a>範例

如果您不正確地訂閱事件，也可能會發生 C3918。 下列範例會產生 C3918。

```cpp
// C3918_3.cpp
// compile with: /clr /c
using namespace System;

public delegate void del();

public ref class A {
public:
   event del^ e {
      void add(del ^handler ) {
         d += handler;
      }

      void remove(del ^handler) {
         d -= handler;
      }

      void raise() {
         d();
      }
   }

   del^ d;
   void f() {}

   A() {
      e = gcnew del(this, &A::f);   // C3918
      // try the following line instead
      // e += gcnew del(this, &A::f);
      e();
   }
};

int main() {
   A a;
}
```
