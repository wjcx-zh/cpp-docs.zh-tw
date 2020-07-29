---
title: 編譯器錯誤 C2319
ms.date: 11/04/2016
f1_keywords:
- C2319
helpviewer_keywords:
- C2319
ms.assetid: 25263e6e-f5ba-4d2c-8727-8c2d8ca2e5ce
ms.openlocfilehash: af9c0f0395e29c384ddc06f9a029f29c921e71c8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221233"
---
# <a name="compiler-error-c2319"></a>編譯器錯誤 C2319

'try/catch' 之後必須是複合陳述式。 遺漏 '{'

在 **`try`** **`catch`** 或語句之後找不到或 **`try`** 區塊 **`catch`** 。 這個區塊必須以大括弧括住。

下列範例會產生 C2319：

```cpp
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
