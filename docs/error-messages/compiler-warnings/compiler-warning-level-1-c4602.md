---
title: 編譯器警告 （層級 1） C4602 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4602
dev_langs:
- C++
helpviewer_keywords:
- C4602
ms.assetid: c1f0300f-e2a2-4c9e-a7c3-4c7318d10509
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3cae5810f94ed9c3feb22de145c7e12e1a7d813b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033312"
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