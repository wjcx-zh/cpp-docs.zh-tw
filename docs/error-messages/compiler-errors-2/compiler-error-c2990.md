---
title: 編譯器錯誤 C2990
ms.date: 11/04/2016
f1_keywords:
- C2990
helpviewer_keywords:
- C2990
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
ms.openlocfilehash: f7327b7d2b0cc9fa4b617a9a6033116c43db6258
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366325"
---
# <a name="compiler-error-c2990"></a>編譯器錯誤 C2990

'class': 非類別類型已被宣告為類別類型

非泛型或樣板類別會重新定義泛型或樣板類別。 請檢查衝突的標頭檔。

下列範例會產生 C2990:

```
// C2990.cpp
// compile with: /c
template <class T>
class C{};
class C{};   // C2990
```

使用泛型時，也會發生 C2990:

```
// C2990b.cpp
// compile with: /clr /c
generic <class T>
ref struct GC;

ref struct GC {};   // C2990
```

C2990 也可能是因為在視覺效果中的重大變更C++視覺效果的編譯器C++2005;編譯器現在會需要多個相同類型的宣告是相同範本規格。

下列範例會產生 C2990:

```
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