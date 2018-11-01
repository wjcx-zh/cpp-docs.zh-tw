---
title: 編譯器錯誤 C2514
ms.date: 11/04/2016
f1_keywords:
- C2514
helpviewer_keywords:
- C2514
ms.assetid: 4b7085e5-6714-4261-80b7-bc72e64ab3e8
ms.openlocfilehash: aef9df0718d013378f88c1a34d08d1b1e05e214c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666997"
---
# <a name="compiler-error-c2514"></a>編譯器錯誤 C2514

'class': 類別有沒有建構函式

類別、 結構或等位有沒有符合用來具現化之參數的參數清單的建構函式。

它可以具現化之前，就必須完全宣告類別。

下列範例會產生 C2514:

```
// C2514.cpp
// compile with: /c
class f;

class g {
public:
    g (int x);
};

class fmaker {
   f *func1() {
      return new f(2);   // C2514
   }

   g *func2() {
      return new g(2);   // OK
   }
};
```