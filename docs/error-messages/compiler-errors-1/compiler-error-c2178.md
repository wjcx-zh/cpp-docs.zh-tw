---
title: 編譯器錯誤 C2178
ms.date: 05/08/2017
f1_keywords:
- C2178
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
ms.openlocfilehash: cd153bb5b331872bfe35b046d41612998bd0eff7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622556"
---
# <a name="compiler-error-c2178"></a>編譯器錯誤 C2178

'*識別碼*'不可以宣告使用'*規範*' 規範

A`mutable`規範使用在宣告中，但在此內容中不允許規範。

`mutable`規範可以只會套用至類別資料成員的名稱，但不可套用至宣告的名稱`const`或`static`，但不可套用至參考的成員。

## <a name="example"></a>範例

下列範例會示範如何 C2178 可能會發生，以及如何修正此問題。

```
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```
