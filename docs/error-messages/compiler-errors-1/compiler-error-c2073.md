---
title: 編譯器錯誤 C2073
ms.date: 11/04/2016
f1_keywords:
- C2073
helpviewer_keywords:
- C2073
ms.assetid: 57908234-be7a-4ce9-b0a7-8b1ad621865e
ms.openlocfilehash: 545b2b24d3bfe5a36c5554dfa898d17b05067c3d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757731"
---
# <a name="compiler-error-c2073"></a>編譯器錯誤 C2073

' identifier '：部分初始化陣列的元素必須有預設的構造函式

為使用者定義型別或常數的陣列指定了太少的初始化運算式。 如果未針對陣列成員指定明確的初始化運算式和其對應的函式，則必須提供預設的函數。

下列範例會產生 C2073：

```cpp
// C2073.cpp
class A {
public:
   A( int );   // constructor for ints only
};
A a[3] = { A(1), A(2) };   // C2073, no default constructor
```

```cpp
// C2073b.cpp
// compile with: /c
class B {
public:
   B();   // default constructor declared
   B( int );
};
B b[3] = { B(1), B(2) };   // OK
```
