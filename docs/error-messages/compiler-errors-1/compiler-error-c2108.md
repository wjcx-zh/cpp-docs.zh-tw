---
title: 編譯器錯誤 C2108
ms.date: 11/04/2016
f1_keywords:
- C2108
helpviewer_keywords:
- C2108
ms.assetid: c84f0b47-5e2c-47d2-8edb-427a40e17c36
ms.openlocfilehash: cbbfa865682ac7423fccd9de4212d901f408810f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214772"
---
# <a name="compiler-error-c2108"></a>編譯器錯誤 C2108

注標不是整數類資料類型

陣列注標是非整數運算式。

## <a name="example"></a>範例

如果您不正確地使用實 **`this`** 數值型別的指標來存取類型的預設索引子，就會發生 C2108。 如需詳細資訊，請參閱[this 指標的語義](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer)。

下列範例會產生 C2108。

```cpp
// C2108.cpp
// compile with: /clr
using namespace System;

value struct B {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
   void Test() {
      Console::WriteLine("{0}", this[3.3]);   // C2108
      Console::WriteLine("{0}", this->default[3.3]);   // OK
   }
};

int main() {
   B ^ myb = gcnew B();
   myb->Test();
}
```
