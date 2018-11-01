---
title: 編譯器錯誤 C3071
ms.date: 11/04/2016
f1_keywords:
- C3071
helpviewer_keywords:
- C3071
ms.assetid: 69879e66-a60e-4058-9bbd-d5c5e2d8ee37
ms.openlocfilehash: 6960dbf62fd30b822f0d7c7a3c46a29a4115913f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428347"
---
# <a name="compiler-error-c3071"></a>編譯器錯誤 C3071

運算子 'operator' 只能套用至 ref 類別或實值類型的執行個體

CLR 運算子不能在原生型別上使用。 運算子可以在 ref 類別或 ref 結構 (實值型別) 上使用，但不能在原生型別上使用，例如 int 或原生型別的別名，例如 System::Int32。 無法從 c + + 程式碼以參考原生變數的方式局限這些型別，因此無法使用運算子。

如需詳細資訊，請參閱 <<c0> [ 追蹤參考運算子](../../windows/tracking-reference-operator-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3071。

```
// C3071.cpp
// compile with: /clr
class N {};
ref struct R {};

int main() {
   N n;
   %n;   // C3071

   R r;
   R ^ r2 = %r;   // OK
}
```