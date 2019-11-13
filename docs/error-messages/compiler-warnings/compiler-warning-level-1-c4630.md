---
title: 編譯器警告（層級1） C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 893364183594782b825377f57fa4e525338d62d8
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052562"
---
# <a name="compiler-warning-level-1-c4630"></a>編譯器警告（層級1） C4630

' symbol '：成員定義上的 ' extern ' 儲存類別規範不合法

資料成員或成員函式定義為 `extern`。 成員不可為外部，雖然整個物件都可以。 編譯器會忽略 `extern` 關鍵字。 下列範例會產生 C4630：

```cpp
// C4630.cpp
// compile with: /W1 /LD
class A {
   void func();
};

extern void A::func() {   // C4630, remove 'extern' to resolve
}
```