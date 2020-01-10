---
title: 編譯器錯誤 C2309
ms.date: 11/04/2016
f1_keywords:
- C2309
helpviewer_keywords:
- C2309
ms.assetid: 6303d5b5-72cf-42b8-92ce-b1eb48e80d48
ms.openlocfilehash: 2567562b5d8a75a40afcb4a94ad453ee65709a00
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759031"
---
# <a name="compiler-error-c2309"></a>編譯器錯誤 C2309

catch 處理常式必須是以括弧括住的例外狀況宣告

Catch 處理常式沒有以括弧括住的類型。

下列範例會產生 C2309：

```cpp
// C2309.cpp
// compile with: /EHsc
#include <eh.h>
class C {};
int main() {
   try {
      throw "ooops!";
   }
   catch C {}   // C2309
   // try the following line instead
   // catch( C ) {}
}
```
