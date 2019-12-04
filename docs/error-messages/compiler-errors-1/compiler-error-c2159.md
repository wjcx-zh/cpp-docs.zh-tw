---
title: 編譯器錯誤 C2159
ms.date: 11/04/2016
f1_keywords:
- C2159
helpviewer_keywords:
- C2159
ms.assetid: 925a2cbd-43c9-45ee-a373-84004350b380
ms.openlocfilehash: 8c0ef75f63f5aa57e02297ebd94d4224048b0f2d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755850"
---
# <a name="compiler-error-c2159"></a>編譯器錯誤 C2159

已經指定一個以上的儲存類別

一個宣告包含多個儲存類別。

下列範例會產生 C2159：

```cpp
// C2159.cpp
// compile with: /c
static int i;   // OK
extern static int i;   // C2159
```
