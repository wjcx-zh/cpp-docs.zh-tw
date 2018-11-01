---
title: 編譯器錯誤 C2319
ms.date: 11/04/2016
f1_keywords:
- C2319
helpviewer_keywords:
- C2319
ms.assetid: 25263e6e-f5ba-4d2c-8727-8c2d8ca2e5ce
ms.openlocfilehash: f0ec35cfb74fd08180969344180ff42d485d58c0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587599"
---
# <a name="compiler-error-c2319"></a>編譯器錯誤 C2319

'try/catch' 之後必須是複合陳述式。 遺漏 '{'

在 `try` 或 `catch` 陳述式後面，找不到 `try` 或 `catch` 區塊。 這個區塊必須以大括弧括住。

下列範例會產生 C2319：

```
// C2319.cpp
// compile with: /EHsc
#include <eh.h>
class C {};
int main() {
   try {
      throw "ooops!";
   }
   catch( C ) ;    // C2319
   // try the following line instead
   // catch( C ) {}
}
```