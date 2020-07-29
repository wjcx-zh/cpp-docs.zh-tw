---
title: 編譯器錯誤 C2646
ms.date: 11/04/2016
f1_keywords:
- C2646
helpviewer_keywords:
- C2646
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
ms.openlocfilehash: a05c98564c4e45dc380690c1b8c9bace5fc14cf4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216150"
---
# <a name="compiler-error-c2646"></a>編譯器錯誤 C2646

位於全域或命名空間範圍的匿名結構或等位必須宣告為 static

匿名結構或等位具有全域或命名空間範圍，但未宣告 **`static`** 。

下列範例會產生 C2646，並示範如何修正此問題。

```cpp
// C2646.cpp
// compile with: /c
union { int i; };   // C2646 not static

// OK
static union { int j; };
union U { int i; };
```
