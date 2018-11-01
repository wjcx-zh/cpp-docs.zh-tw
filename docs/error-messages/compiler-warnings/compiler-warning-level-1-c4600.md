---
title: 編譯器警告 (層級 1) C4600
ms.date: 11/04/2016
f1_keywords:
- C4600
helpviewer_keywords:
- C4600
ms.assetid: f023a2a1-7fc4-463f-a434-dc93fcd3f4e9
ms.openlocfilehash: fcfefd5b858df653551e7f3061a41d168c8ff3f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50489605"
---
# <a name="compiler-warning-level-1-c4600"></a>編譯器警告 (層級 1) C4600

\#pragma '巨集名稱': 必須是有效的非空白字串

當您推送或快顯使用巨集名稱時，不能指定空字串[pop_macro](../../preprocessor/pop-macro.md)或是[push_macro](../../preprocessor/push-macro.md)。

下列範例會產生 C4600:

```
// C4600.cpp
// compile with: /W1
int main()
{
   #pragma push_macro("")   // C4600 passing an empty string
}
```