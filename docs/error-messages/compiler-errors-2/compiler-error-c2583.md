---
title: 編譯器錯誤 C2583
ms.date: 11/04/2016
f1_keywords:
- C2583
helpviewer_keywords:
- C2583
ms.assetid: b1c952dc-872c-47e4-9fc8-4dd72bcee6f9
ms.openlocfilehash: b78b9dd69b701e1a66646234d4603973657e90c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597973"
---
# <a name="compiler-error-c2583"></a>編譯器錯誤 C2583

'identifier': 'const/volatile' 'this' 指標不合法的建構函式/解構函式

宣告建構函式或解構函式`const`或`volatile`。 這是不允許的。

下列範例會產生 C2583:

```
// C2583.cpp
// compile with: /c
class A {
public:
   int i;
   A() const;   // C2583

   // try the following line instead
   // A();
};
```