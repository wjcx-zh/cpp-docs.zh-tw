---
title: 編譯器警告 (層級 1) C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 3a533afe141a465fb034ba7d90b22a8206bf0910
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230619"
---
# <a name="compiler-warning-level-1-c4630"></a>編譯器警告 (層級 1) C4630

' symbol '：成員定義上的 ' extern ' 儲存類別規範不合法

資料成員或成員函式定義為 **`extern`** 。 成員不可為外部，雖然整個物件都可以。 編譯器會忽略 **`extern`** 關鍵字。 下列範例會產生 C4630：

```cpp
// C4630.cpp
// compile with: /W1 /LD
class A {
   void func();
};

extern void A::func() {   // C4630, remove 'extern' to resolve
}
```
