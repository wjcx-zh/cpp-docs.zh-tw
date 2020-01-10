---
title: 編譯器警告 (層級 1) C4602
ms.date: 11/04/2016
f1_keywords:
- C4602
helpviewer_keywords:
- C4602
ms.assetid: c1f0300f-e2a2-4c9e-a7c3-4c7318d10509
ms.openlocfilehash: 7cacadea560dc5a68d396ac607deb3a5a3c236ee
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965907"
---
# <a name="compiler-warning-level-1-c4602"></a>編譯器警告 (層級 1) C4602

\#pragma pop_macro： ' 宏名稱 ' 沒有此識別碼的上一個 #pragma push_macro

如果您使用特定巨集的 [pop_macro](../../preprocessor/pop-macro.md) ，則必須先將該巨集名稱傳遞給 [push_macro](../../preprocessor/push-macro.md)。 例如，下列範例會產生 C4602：

```cpp
// C4602.cpp
// compile with: /W1
int main()
{
   #pragma pop_macro("x")   // C4602 x is not on the stack
}
```