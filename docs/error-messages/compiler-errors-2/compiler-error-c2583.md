---
title: 編譯器錯誤 C2583
ms.date: 11/04/2016
f1_keywords:
- C2583
helpviewer_keywords:
- C2583
ms.assetid: b1c952dc-872c-47e4-9fc8-4dd72bcee6f9
ms.openlocfilehash: b78b9dd69b701e1a66646234d4603973657e90c6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366390"
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