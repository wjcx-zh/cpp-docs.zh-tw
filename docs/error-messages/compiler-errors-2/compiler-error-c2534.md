---
title: 編譯器錯誤 C2534
ms.date: 11/04/2016
f1_keywords:
- C2534
helpviewer_keywords:
- C2534
ms.assetid: 481f9f54-5b51-4aa0-8eea-218f10807705
ms.openlocfilehash: 4b1e481c733f52b0be419b7fd786b26a90362f9c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737085"
---
# <a name="compiler-error-c2534"></a>編譯器錯誤 C2534

' identifier '：函式無法傳回值

函式無法傳回值或具有傳回類型（甚至不是 `void` 傳回類型）。

藉由從函式定義中移除 `return` 語句，即可修正此錯誤。

下列範例會產生 C2534：

```cpp
// C2534.cpp
class A {
public:
   int i;
   A() { return i; }   // C2534
};
```
