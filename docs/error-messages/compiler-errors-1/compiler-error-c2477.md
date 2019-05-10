---
title: 編譯器錯誤 C2477
ms.date: 11/04/2016
f1_keywords:
- C2477
helpviewer_keywords:
- C2477
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
ms.openlocfilehash: 73d8daa9576e4edc29958918c107e9edf18cc579
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447967"
---
# <a name="compiler-error-c2477"></a>編譯器錯誤 C2477

'member': 無法透過衍生類別初始化靜態資料成員

樣板類別的靜態資料成員初始化不正確。 這是一項重大變更與版本的 MicrosoftC++在 Visual Studio.NET 2003 中，以符合 ISO 之前的編譯器C++標準。

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