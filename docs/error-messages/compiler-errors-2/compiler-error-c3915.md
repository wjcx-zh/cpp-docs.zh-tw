---
title: 編譯器錯誤 C3915
ms.date: 11/04/2016
f1_keywords:
- C3915
helpviewer_keywords:
- C3915
ms.assetid: 2b0a5e5f-3aec-4a4b-9157-233031817084
ms.openlocfilehash: 511da8ebe896cb2d0e2869f36bdb474cae5ba521
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507753"
---
# <a name="compiler-error-c3915"></a>編譯器錯誤 C3915

'type' 中有任何預設索引屬性 （類別索引子）

類型沒有預設值，索引的屬性。

如需詳細資訊，請參閱 [property](../../windows/property-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3915。

```
// C3915.cpp
// compile with: /clr
ref class X {
public:
// uncomment property to resolve this C3915
//   property int default[]
//   {
//      int get(int i)
//      {
//         return 863;
//      }
//   }
};

int main() {
   X^ x = new X;
   System::Console::WriteLine(x[1]);   // C3915
}
```

## <a name="example"></a>範例

如果您嘗試使用預設索引子，其定義與所在的相同編譯，也會發生 C3915 <xref:System.Reflection.DefaultMemberAttribute>。

下列範例會產生 C3915。

```
// C3915_b.cpp
// compile with: /clr
using namespace System;

[Reflection::DefaultMember("XXX")]
ref struct A {
   property Double XXX[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
};

ref struct B {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
};

int main() {
   A ^ mya = gcnew A();
   Console::WriteLine("{0}", mya[3]);   // C3915

   B ^ myb = gcnew B();
   Console::WriteLine("{0}", myb[3]);   // OK
}
```