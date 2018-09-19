---
title: 編譯器錯誤 C2694 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2694
dev_langs:
- C++
helpviewer_keywords:
- C2694
ms.assetid: 8dc2cec2-67ae-4e16-8c0c-374425aca8bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aae194d0ec2aa6c5eedafa1d4c66137861385ed6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029583"
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