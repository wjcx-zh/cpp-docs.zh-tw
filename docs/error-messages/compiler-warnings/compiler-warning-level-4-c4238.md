---
title: 編譯器警告 (層級 4) C4238
ms.date: 11/04/2016
f1_keywords:
- C4238
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
ms.openlocfilehash: c5ffa07b06f010d10edc14aa7576bb614aa9dd04
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471899"
---
# <a name="compiler-warning-level-4-c4238"></a>編譯器警告 (層級 4) C4238

使用非標準擴充： 類別右值當做左值

與舊版的 Visual c + + 中，Microsoft 擴充功能的相容性 (**/Ze**) 可讓您使用的類別類型，因為在內容中的右值也會隱含或明確地取得其位址。 在某些情況下，如下列範例中，這很危險。

## <a name="example"></a>範例

```
// C4238.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

C * pC = &C();   // C4238
```

這種用法會導致 ANSI 相容性錯誤 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。