---
title: 編譯器錯誤 C2676
ms.date: 11/04/2016
f1_keywords:
- C2676
helpviewer_keywords:
- C2676
ms.assetid: 838a5e34-c92f-4f65-a597-e150bf8cf737
ms.openlocfilehash: 9c25593df27f7c4e742eb109aeb5e94ba6fdba8c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760357"
---
# <a name="compiler-error-c2676"></a>編譯器錯誤 C2676

二元 ' operator '： ' type ' 未定義此運算子或預先定義運算子可接受的類型轉換

若要使用運算子，您必須針對指定類型進行多載，或針對已定義運算子的類型定義轉換。

## <a name="example"></a>範例

下列範例會產生 C2676。

```cpp
// C2676.cpp
// C2676 expected
struct C {
   C();
} c;

struct D {
   D();
   D operator >>( C& ){return * new D;}
   D operator <<( C& ){return * new D;}
} d;

struct E {
   // operator int();
};

int main() {
   d >> c;
   d << c;
   E e1, e2;
   e1 == e2;   // uncomment operator int in class E, then
               // it is OK even though neither E::operator==(E) nor
               // operator==(E, E) defined. Uses the conversion to int
               // and then the builtin-operator==(int, int)
}
```

## <a name="example"></a>範例

如果您嘗試在參考型別的 `this` 指標上執行指標算術，也可能會發生 C2676。

`this` 指標是參考型別中的類型控制碼。 如需詳細資訊，請參閱[this 指標的語義](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer)。

下列範例會產生 C2676。

```cpp
// C2676_a.cpp
// compile with: /clr
using namespace System;

ref struct A {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }

   A() {
      Console::WriteLine("{0}", this + 3.3);   // C2676
      Console::WriteLine("{0}", this[3.3]);   // OK
   }
};

int main() {
   A ^ mya = gcnew A();
}
```
