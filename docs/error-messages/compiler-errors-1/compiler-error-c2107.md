---
title: 編譯器錯誤 C2107
ms.date: 11/04/2016
f1_keywords:
- C2107
helpviewer_keywords:
- C2107
ms.assetid: 2866a121-884e-4bb5-8613-36de5817000e
ms.openlocfilehash: 2b388495c6ce31452bd3f8e8bfc6c26a6bfbdbe8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643023"
---
# <a name="compiler-error-c2107"></a>編譯器錯誤 C2107

不合法的索引，不允許間接取值

註標會套用至運算式未評估的指標。

## <a name="example"></a>範例

如果您不當使用，就會發生 C2107`this`存取類型的預設索引子實值類型的指標。 如需詳細資訊，請參閱 <<c0> [ 語意的 this 指標](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer)。

下列範例會產生 C2107。

```
// C2107.cpp
// compile with: /clr
using namespace System;

value struct B {
   property String ^ default[String ^] {
      String ^ get(String ^ data) {
         return "abc";
      }
   }
   void Test() {
      Console::WriteLine("{0}", this["aa"]);   // C2107
      Console::WriteLine("{0}", this->default["aa"]);   // OK
   }
};

int main() {
   B ^ myb = gcnew B();
   myb->Test();
}
```