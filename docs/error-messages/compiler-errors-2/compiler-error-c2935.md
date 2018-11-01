---
title: 編譯器錯誤 C2935
ms.date: 11/04/2016
f1_keywords:
- C2935
helpviewer_keywords:
- C2935
ms.assetid: e11ef90d-0756-4e43-8a09-4974c6aa72a3
ms.openlocfilehash: f44a8060910b1aeeaa4b85d1df081a559e720df8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549652"
---
# <a name="compiler-error-c2935"></a>編譯器錯誤 C2935

'class': type-class-id 重複定義為全域函式

您無法使用泛型或樣板類別作為全域函式。

此錯誤可能是大括弧不對稱所造成。

下列範例會產生 C2935：

```
// C2935.cpp
// compile with: /c
template<class T>
struct TC {};
void TC<int>() {}   // C2935

// OK
struct TC2 {};
void TC2() {}
```

使用泛型時，也會發生 C2935：

```
// C2935b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC { };
void GC<int>() {}   // C2935
void GC() {}   // OK
```