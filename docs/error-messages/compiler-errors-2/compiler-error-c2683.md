---
title: 編譯器錯誤 C2683
ms.date: 11/04/2016
f1_keywords:
- C2683
helpviewer_keywords:
- C2683
ms.assetid: db605e4f-601b-4d05-92a1-c43ca24de08d
ms.openlocfilehash: 49e4897ad5db866aa1ca42589859bedff12718df
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625152"
---
# <a name="compiler-error-c2683"></a>編譯器錯誤 C2683

'cast': 'type' 不是多型類型

您無法使用[dynamic_cast](../../cpp/dynamic-cast-operator.md)轉換為非多型的類別 （具有虛擬函式的類別）。

您可以使用[static_cast](../../cpp/static-cast-operator.md)執行非多型類型的轉換。 不過，`static_cast`不會執行執行階段檢查。

下列範例會產生 C2683:

```
// C2683.cpp
// compile with: /c
class B { };
class D : public B { };

void f(B* pb) {
   D* pd1 = dynamic_cast<D*>(pb);  // C2683
   D* pd1 = static_cast<D*>(pb);   // OK
}
```