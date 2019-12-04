---
title: 編譯器錯誤 C2694
ms.date: 11/04/2016
f1_keywords:
- C2694
helpviewer_keywords:
- C2694
ms.assetid: 8dc2cec2-67ae-4e16-8c0c-374425aca8bc
ms.openlocfilehash: ca378c3e0ce88b454cb89fc08470a277a7be6f47
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755222"
---
# <a name="compiler-error-c2694"></a>編譯器錯誤 C2694

' override '：覆寫虛擬函式的例外狀況規格比基類虛擬成員函式 ' base ' 的限制少

已覆寫虛擬函式，但在[/za](../../build/reference/za-ze-disable-language-extensions.md)底下，覆寫函式的[例外狀況規格](../../cpp/exception-specifications-throw-cpp.md)較不嚴格。

下列範例會產生 C2694：

```cpp
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
