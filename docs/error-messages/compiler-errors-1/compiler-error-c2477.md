---
title: 編譯器錯誤 C2477
ms.date: 11/04/2016
f1_keywords:
- C2477
helpviewer_keywords:
- C2477
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
ms.openlocfilehash: aa276ea839f11574609b183d78b46e08581a1b51
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743649"
---
# <a name="compiler-error-c2477"></a>編譯器錯誤 C2477

' member '：靜態資料成員無法透過衍生類別初始化

範本類別的靜態資料成員未正確初始化。 在 Visual Studio .NET 2003 之前，這是 Microsoft C++編譯器版本的重大變更，以符合 ISO C++標準。

下列範例會產生 C2477：

```cpp
// C2477.cpp
// compile with: /Za /c
template <class T>
struct S {
   static int n;
};

struct X {};
struct A: S<X> {};

int A::n = 0;   // C2477

template<>
int S<X>::n = 0;
```
