---
title: 編譯器警告 (層級 1) C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 414388fc1b9c6a7425d45e2ba92546960cadf404
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199611"
---
# <a name="compiler-warning-level-1-c4630"></a>編譯器警告 (層級 1) C4630

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
