---
title: 編譯器錯誤 C3865
ms.date: 11/04/2016
f1_keywords:
- C3865
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
ms.openlocfilehash: 960c795fe934433e4e3cf79e4c01c49d00205b9b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761487"
---
# <a name="compiler-error-c3865"></a>編譯器錯誤 C3865

' calling_convention '：只能用在原生成員函式上

呼叫慣例是在全域函式或 managed 成員函式的函式上使用。 呼叫慣例只能用在原生（非受控）成員函式上。

如需詳細資訊，請參閱[呼叫慣例](../../cpp/calling-conventions.md)。

下列範例會產生 C3865：

```cpp
// C3865.cpp
// compile with: /clr
// processor: x86
void __thiscall Func(){}   // C3865

// OK
struct MyType {
   void __thiscall Func(){}
};
```
