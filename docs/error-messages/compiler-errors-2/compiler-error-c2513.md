---
title: 編譯器錯誤 C2513
ms.date: 11/04/2016
f1_keywords:
- C2513
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
ms.openlocfilehash: 13840246a5dc6a1c1bdbcb55dc47f212ee353d81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561196"
---
# <a name="compiler-error-c2513"></a>編譯器錯誤 C2513

'type': '=' 之前沒有宣告變數

類型指定名稱會出現在任何變數的識別項的宣告。

下列範例會產生 C2513:

```
// C2513.cpp
int main() {
   int = 9;   // C2513
   int i = 9;   // OK
}
```

這項錯誤也可能導致 Visual Studio.NET 2003年所進行的編譯器一致性工作： 初始化 typedef，不再允許。 初始化 typedef 標準不允許的而且現在會產生編譯器錯誤。

```
// C2513b.cpp
// compile with: /c
typedef struct S {
   int m_i;
} S = { 1 };   // C2513
// try the following line instead
// } S;
```

另外，也可以刪除`typedef`來定義變數，以彙總初始設定式清單中，但這不建議，因為它會建立具有相同名稱做為類型的變數，並隱藏的類型名稱。