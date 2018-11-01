---
title: 編譯器警告 (層級 1) C4602
ms.date: 11/04/2016
f1_keywords:
- C4602
helpviewer_keywords:
- C4602
ms.assetid: c1f0300f-e2a2-4c9e-a7c3-4c7318d10509
ms.openlocfilehash: c719ae23ed3799debf2db9c8f2d82b3c49db3156
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430384"
---
# <a name="compiler-warning-level-1-c4602"></a>編譯器警告 (層級 1) C4602

\#pragma pop_macro: '巨集名稱' #pragma push_macro，此識別項

如果您使用特定巨集的 [pop_macro](../../preprocessor/pop-macro.md) ，則必須先將該巨集名稱傳遞給 [push_macro](../../preprocessor/push-macro.md)。 例如，下列範例會產生 C4602：

```
// C4602.cpp
// compile with: /W1
int main()
{
   #pragma pop_macro("x")   // C4602 x is not on the stack
}
```