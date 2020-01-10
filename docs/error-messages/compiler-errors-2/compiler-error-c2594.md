---
title: 編譯器錯誤 C2594
ms.date: 11/04/2016
f1_keywords:
- C2594
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
ms.openlocfilehash: ade657f9ada2a2249d2f96b7caada7b9719195d1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759330"
---
# <a name="compiler-error-c2594"></a>編譯器錯誤 C2594

' operator '：不明確地將 ' type1 ' 轉換為 ' type2 '

從*type1*到*type2*的轉換不是任何其他的直接。 我們建議兩個可能的解決方案，以從*type1*轉換成*type2*。 第一個選項是定義從*type1*到*type2*的直接轉換，第二個選項是指定從*type1*轉換成*type2*的順序。

下列範例會產生 C2594。 建議的錯誤解決方式是轉換的序列：

```cpp
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
