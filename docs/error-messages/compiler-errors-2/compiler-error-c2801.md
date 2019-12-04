---
title: 編譯器錯誤 C2801
ms.date: 11/04/2016
f1_keywords:
- C2801
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
ms.openlocfilehash: 0d2ea3677d883fa4843c37a41d733872b23cbba0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760669"
---
# <a name="compiler-error-c2801"></a>編譯器錯誤 C2801

' operator operator ' 必須是非靜態成員

下列運算子只能多載為非靜態成員：

- 指派 `=`

- 類別成員存取 `->`

- 注標 `[]`

- 函式呼叫 `()`

可能的 C2801 原因：

- 多載運算子不是類別、結構或等位成員。

- 已將多載的運算子宣告 `static`。

- 下列範例會產生 C2801：

```cpp
// C2801.cpp
// compile with: /c
operator[]();   // C2801 not a member
class A {
   static operator->();   // C2801 static
   operator()();   // OK
};
```
