---
title: 編譯器錯誤 C2627
ms.date: 11/04/2016
f1_keywords:
- C2627
helpviewer_keywords:
- C2627
ms.assetid: 7fc6c5ac-c7c9-4f0b-ad52-f52252526458
ms.openlocfilehash: 6b0471aaead1b56f51e4393784306aa6ed928eec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754728"
---
# <a name="compiler-error-c2627"></a>編譯器錯誤 C2627

' function '：匿名等位中不允許成員函式

[匿名聯集](../../cpp/unions.md#anonymous_unions)不能有成員函式。

下列範例會產生 C2627：

```cpp
// C2627.cpp
int main() {
   union { void f(){} };   // C2627
   union X { void f(){} };
}
```
