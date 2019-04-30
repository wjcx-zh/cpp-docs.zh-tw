---
title: 編譯器警告 (層級 4) C4238
ms.date: 11/04/2016
f1_keywords:
- C4238
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
ms.openlocfilehash: c5ffa07b06f010d10edc14aa7576bb614aa9dd04
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401029"
---
# <a name="compiler-warning-level-4-c4238"></a>編譯器警告 (層級 4) C4238

使用非標準擴充： 類別右值當做左值

與舊版的視覺效果的相容性C++，Microsoft 擴充功能 (**/Ze**) 可讓您使用的類別類型，因為在內容中的右值也會隱含或明確地取得其位址。 在某些情況下，如下列範例中，這很危險。

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