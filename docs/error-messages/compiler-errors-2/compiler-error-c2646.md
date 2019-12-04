---
title: 編譯器錯誤 C2646
ms.date: 11/04/2016
f1_keywords:
- C2646
helpviewer_keywords:
- C2646
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
ms.openlocfilehash: a5c4dbc967c304fc6b13eb00e2c7093380ec8be9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758212"
---
# <a name="compiler-error-c2646"></a>編譯器錯誤 C2646

位於全域或命名空間範圍的匿名結構或等位必須宣告為 static

位於全域或命名空間範圍但未宣告為 `static` 的匿名結構或等位。

下列範例會產生 C2646，並示範如何修正此問題。

```cpp
// C2646.cpp
// compile with: /c
union { int i; };   // C2646 not static

// OK
static union { int j; };
union U { int i; };
```
