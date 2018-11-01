---
title: 編譯器錯誤 C2462
ms.date: 11/04/2016
f1_keywords:
- C2462
helpviewer_keywords:
- C2462
ms.assetid: a8601bf8-f5ce-41de-9117-e2632bd4996b
ms.openlocfilehash: 0b342f8b878c48a77336fab4921cf4a668e248ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607047"
---
# <a name="compiler-error-c2462"></a>編譯器錯誤 C2462

'identifier': 無法在 'new-expression' 中定義的類型

您無法定義類型的運算元欄位在`new`運算子。 型別定義置於個別的陳述式。

下列範例會產生 C2462:

```
// C2462.cpp
int main() {
   new struct S { int i; };   // C2462
}
```