---
title: 編譯器警告（層級1） C4544
ms.date: 11/04/2016
f1_keywords:
- C4544
helpviewer_keywords:
- C4544
ms.assetid: 11ee04df-41ae-435f-af44-881e801315a8
ms.openlocfilehash: 094662270569c7362b7bb3c4953a466b19ed2e65
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966476"
---
# <a name="compiler-warning-level-1-c4544"></a>編譯器警告（層級1） C4544

declaration'：在這個樣板宣告上已忽略的預設樣板引數

在不正確的位置中指定預設樣板引數，並且已將其忽略。 類別樣板的預設樣板引數只能在宣告或類別樣板定義中指定，而不會在類別樣板的成員上指定。

此範例會產生 C4545，而下一個範例會顯示如何修正它：

```cpp
// C4544.cpp
// compile with: /W1 /LD
template <class T>
struct S
{
   template <class T1>
      struct S1;
   void f();
};

template <class T=int>
template <class T1>
struct S<T>::S1 {};   // C4544
```

在此範例中，預設參數會套用至類別樣板 `S`：

```cpp
// C4544b.cpp
// compile with: /LD
template <class T = int>
struct S
{
   template <class T1>
      struct S1;
   void f();
};

template <class T>
template <class T1>
struct S<T>::S1 {};
```