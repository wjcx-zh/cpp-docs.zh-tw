---
title: 編譯器錯誤 C2477
ms.date: 11/04/2016
f1_keywords:
- C2477
helpviewer_keywords:
- C2477
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
ms.openlocfilehash: 27db194cb308d711a259127b628c60b4d10b94ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383226"
---
# <a name="compiler-error-c2477"></a>編譯器錯誤 C2477

'member': 無法透過衍生類別初始化靜態資料成員

樣板類別的靜態資料成員初始化不正確。 這是一項重大變更，與新版視覺效果C++在 Visual Studio.NET 2003 中，以符合 ISO 之前的編譯器C++標準。

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