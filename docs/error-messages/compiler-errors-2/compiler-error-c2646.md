---
title: 編譯器錯誤 C2646
ms.date: 11/04/2016
f1_keywords:
- C2646
helpviewer_keywords:
- C2646
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
ms.openlocfilehash: c02d7216df42681ae2ec733ae932d22861c1f0ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571999"
---
# <a name="compiler-error-c2646"></a>編譯器錯誤 C2646

位於全域或命名空間範圍的匿名結構或等位必須宣告為 static

位於全域或命名空間範圍但未宣告為 `static` 的匿名結構或等位。

下列範例會產生 C2646，並示範如何修正此問題。

```
// C2646.cpp
// compile with: /c
union { int i; };   // C2646 not static

// OK
static union { int j; };
union U { int i; };
```