---
title: 編譯器錯誤 C2694
ms.date: 11/04/2016
f1_keywords:
- C2694
helpviewer_keywords:
- C2694
ms.assetid: 8dc2cec2-67ae-4e16-8c0c-374425aca8bc
ms.openlocfilehash: 4897512f6bd27465b7281d7a27757918128202d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367742"
---
# <a name="compiler-error-c2694"></a>編譯器錯誤 C2694

'override': 覆寫虛擬函式的較不嚴格的例外狀況規格比基底類別虛擬成員函式 'base'

虛擬函式已遭覆寫，但底下[/Za](../../build/reference/za-ze-disable-language-extensions.md)，則覆寫函式有較不嚴格[例外狀況規格](../../cpp/exception-specifications-throw-cpp.md)。

下列範例會產生 C2694:

```
// C2694.cpp
// compile with: /Za /c
class MyBase {
public:
   virtual void f(void) throw(int) {
   }
};

class Derived : public MyBase {
public:
   void f(void) throw(...) {}   // C2694
   void f2(void) throw(int) {}   // OK
};
```