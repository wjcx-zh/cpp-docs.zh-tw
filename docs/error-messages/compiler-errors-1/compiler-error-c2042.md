---
title: 編譯器錯誤 C2042
ms.date: 11/04/2016
f1_keywords:
- C2042
helpviewer_keywords:
- C2042
ms.assetid: e111788f-41ce-405a-9824-a4c1c26059e6
ms.openlocfilehash: 3302b3a529ad8af054bb29bced66bc939abcc060
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643858"
---
# <a name="compiler-error-c2042"></a>編譯器錯誤 C2042

signed 及 unsigned 關鍵字是互斥的

關鍵字 `signed` 和 `unsigned` 用於單一宣告中。

下列範例會產生 C2042：

```
// C2042.cpp
unsigned signed int i;   // C2042
```

可能的解決方式：

```
// C2042b.cpp
// compile with: /c
unsigned int i;
signed int ii;
```