---
title: 編譯器錯誤 C2178
ms.date: 05/08/2017
f1_keywords:
- C2178
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
ms.openlocfilehash: 4904c7009151748b4585060c816e0bd5c407be33
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225549"
---
# <a name="compiler-error-c2178"></a>編譯器錯誤 C2178

'*identifier*' 不能以 '*規範*' 規範宣告

在宣告中使用了指定名稱 **`mutable`** ，但在此內容中不允許規範。

規範只能套用 **`mutable`** 至類別資料成員的名稱，而且不能套用至宣告為或的名稱，也不能套用 **`const`** **`static`** 至參考成員。

## <a name="example"></a>範例

下列範例會顯示 C2178 的發生方式，以及如何修正此問題。

```cpp
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```
