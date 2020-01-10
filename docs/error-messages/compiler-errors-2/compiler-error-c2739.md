---
title: 編譯器錯誤 C2739
ms.date: 11/04/2016
f1_keywords:
- C2739
helpviewer_keywords:
- C2739
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
ms.openlocfilehash: 18cece8d9630aa93e867329acc7cefea30da3286
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759655"
---
# <a name="compiler-error-c2739"></a>編譯器錯誤 C2739

'number'：明確的 Managed 或 WinRT 陣列維度必須是介於 1 到 32 之間

陣列維度不是介於 1 到 32 之間。

下列範例會產生 C2739，並示範如何修正此問題：

```cpp
// C2739.cpp
// compile with: /clr
int main() {
   array<int, -1>^a;   // C2739
   // try the following line instead
   // array<int, 2>^a;
}
```
