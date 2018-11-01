---
title: 編譯器錯誤 C2477
ms.date: 11/04/2016
f1_keywords:
- C2477
helpviewer_keywords:
- C2477
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
ms.openlocfilehash: 27db194cb308d711a259127b628c60b4d10b94ff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458158"
---
# <a name="compiler-error-c2477"></a>編譯器錯誤 C2477

'member': 無法透過衍生類別初始化靜態資料成員

樣板類別的靜態資料成員初始化不正確。 這是為了符合 ISO c + + 標準的一項重大變更與 Visual Studio.NET 2003年之前的 Visual c + + 編譯器的版本。

下列範例會產生 C2477:

```
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