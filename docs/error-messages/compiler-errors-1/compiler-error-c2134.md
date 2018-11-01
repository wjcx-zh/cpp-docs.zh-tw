---
title: 編譯器錯誤 C2134
ms.date: 11/04/2016
f1_keywords:
- C2134
ms.assetid: d45cb3e8-0be4-4bd6-8be9-5f8d2384363f
ms.openlocfilehash: 8bb472cc7864e597404394ac7c80468e1cd59f5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595932"
---
# <a name="compiler-error-c2134"></a>編譯器錯誤 C2134

'function': 呼叫不會產生常數運算式

宣告為 constexpr 只能呼叫其他函式的函式宣告為 constexpr。

下列範例會產生 C2134:

```
// C2134.cpp
// compile with: /c
int A() {
    return 42;
};

constexpr int B() {
    return A();  // Error C2134: 'A': call does not result in a constant expression.
}
```

可能的解決方式：

```
// C2134b.cpp
constexpr int A() {  // add constexpr to A, since it meets the requirements of constexpr.
    return 42;
};

constexpr int B() {
    return A();  // No error
}
```