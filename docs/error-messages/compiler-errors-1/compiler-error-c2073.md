---
title: 編譯器錯誤 C2073
ms.date: 11/04/2016
f1_keywords:
- C2073
helpviewer_keywords:
- C2073
ms.assetid: 57908234-be7a-4ce9-b0a7-8b1ad621865e
ms.openlocfilehash: 2b45d512224ec32459e6da040a6abb0211278e78
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523271"
---
# <a name="compiler-error-c2073"></a>編譯器錯誤 C2073

'identifier': 部分初始化陣列的項目必須具有預設建構函式

指定的使用者定義型別或常數陣列初始設定式太少。 如果陣列成員未指定明確的初始設定式和其對應的建構函式，則必須提供預設建構函式。

下列範例會產生 C2073:

```
// C2073.cpp
class A {
public:
   A( int );   // constructor for ints only
};
A a[3] = { A(1), A(2) };   // C2073, no default constructor
```

```
// C2073b.cpp
// compile with: /c
class B {
public:
   B();   // default constructor declared
   B( int );
};
B b[3] = { B(1), B(2) };   // OK
```