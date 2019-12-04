---
title: 編譯器錯誤 C2683
ms.date: 11/04/2016
f1_keywords:
- C2683
helpviewer_keywords:
- C2683
ms.assetid: db605e4f-601b-4d05-92a1-c43ca24de08d
ms.openlocfilehash: 8526dc1fe3cacc872aa91ca058677d15318fd703
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760266"
---
# <a name="compiler-error-c2683"></a>編譯器錯誤 C2683

' cast '： ' type ' 不是多型類型

您無法使用[dynamic_cast](../../cpp/dynamic-cast-operator.md)從非多型類別（沒有虛擬函式的類別）進行轉換。

您可以使用[static_cast](../../cpp/static-cast-operator.md)來執行非多型類型的轉換。 不過，`static_cast` 不會執行執行時間檢查。

下列範例會產生 C2683：

```cpp
// C2683.cpp
// compile with: /c
class B { };
class D : public B { };

void f(B* pb) {
   D* pd1 = dynamic_cast<D*>(pb);  // C2683
   D* pd1 = static_cast<D*>(pb);   // OK
}
```
