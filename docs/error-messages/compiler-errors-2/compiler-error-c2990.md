---
title: 編譯器錯誤 C2990
ms.date: 11/04/2016
f1_keywords:
- C2990
helpviewer_keywords:
- C2990
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
ms.openlocfilehash: 1c58c2d5da0049ec670e11c930b397caec3cbbee
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751517"
---
# <a name="compiler-error-c2990"></a>編譯器錯誤 C2990

' class '：已經宣告為類別類型的非類別類型

非泛型或範本類別會重新定義泛型或樣板類別。 檢查標頭檔是否有衝突。

下列範例會產生 C2990：

```cpp
// C2990.cpp
// compile with: /c
template <class T>
class C{};
class C{};   // C2990
```

使用泛型時，也會發生 C2990：

```cpp
// C2990b.cpp
// compile with: /clr /c
generic <class T>
ref struct GC;

ref struct GC {};   // C2990
```

C2990 也可能是因為 Microsoft C++編譯器中的 Visual Studio 2005 的重大變更所造成;編譯器現在需要相同類型的多個宣告與範本規格有關。

下列範例會產生 C2990：

```cpp
// C2990c.cpp
// compile with: /c
template<class T>
class A;

template<class T>
struct A2 {
   friend class A;   // C2990
};

// OK
template<class T>
struct B {
   template<class T>
   friend class A;
};
```
