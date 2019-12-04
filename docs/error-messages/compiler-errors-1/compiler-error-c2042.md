---
title: 編譯器錯誤 C2042
ms.date: 11/04/2016
f1_keywords:
- C2042
helpviewer_keywords:
- C2042
ms.assetid: e111788f-41ce-405a-9824-a4c1c26059e6
ms.openlocfilehash: 6bc66f5b3a7bd669ef06cac3b53631ff7948e8ad
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740386"
---
# <a name="compiler-error-c2042"></a>編譯器錯誤 C2042

signed 及 unsigned 關鍵字是互斥的

關鍵字 `signed` 和 `unsigned` 用於單一宣告中。

下列範例會產生 C2042：

```cpp
// C2042.cpp
unsigned signed int i;   // C2042
```

可能的解決方案：

```cpp
// C2042b.cpp
// compile with: /c
unsigned int i;
signed int ii;
```
