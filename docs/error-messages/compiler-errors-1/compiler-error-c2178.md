---
title: 編譯器錯誤 C2178
ms.date: 05/08/2017
f1_keywords:
- C2178
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
ms.openlocfilehash: 85cac4919c048c30a3ed1ff5573a3c14b77da0bd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737188"
---
# <a name="compiler-error-c2178"></a>編譯器錯誤 C2178

'*identifier*' 不能以 '*規範*' 規範宣告

宣告中使用了 `mutable` 規範，但此內容中不允許指定規范。

`mutable` 規範只能套用至類別資料成員的名稱，而且不能套用至宣告 `const` 或 `static`的名稱，而且也不能套用至參考成員。

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
