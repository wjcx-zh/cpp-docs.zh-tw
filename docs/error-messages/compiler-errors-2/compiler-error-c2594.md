---
title: 編譯器錯誤 C2594
ms.date: 11/04/2016
f1_keywords:
- C2594
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
ms.openlocfilehash: 75e3b438dd69f8879fdc2273a8f0357229941340
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428281"
---
# <a name="compiler-error-c2594"></a>編譯器錯誤 C2594

'operator': 從 'type1' 模稜兩可的轉換成 'type2'

沒有從轉換*type1*要*type2*是比其他任何更直接。 我們建議兩個可能的解決方案從轉換*type1*要*type2*。 第一個選項是定義從直接轉換*type1*要*type2*，和第二個選項是指定的轉換，從序列*type1*至*type2*。

下列範例會產生 C2594。 錯誤的建議解決方式是一連串的轉換：

```
// C2594.cpp
// compile with: /c
struct A{};
struct I1 : A {};
struct I2 : A {};
struct D : I1, I2 {};

A *f (D *p) {
   return (A*) (p);    // C2594

// try the following line instead
// return static_cast<A *>(static_cast<I1 *>(p));
}
```