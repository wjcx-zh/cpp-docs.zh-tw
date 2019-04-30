---
title: 編譯器錯誤 C2911
ms.date: 11/04/2016
f1_keywords:
- C2911
helpviewer_keywords:
- C2911
ms.assetid: 83c7c01a-ab6a-4179-9fb0-289a9ec8d44e
ms.openlocfilehash: 56977f481a77c1f5865bec5d6ecc01c99d8224cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408468"
---
# <a name="compiler-error-c2911"></a>編譯器錯誤 C2911

'member' : 無法在目前的範圍中宣告或定義

您只能在命名空間、類別或函式之中，定義相同命名空間、類別或函式的成員，或者是由相同命名空間、類別或函式封入的成員。

下列範例會產生 C2911：

```
// C2911.cpp
struct A;

namespace M {
   struct D;
}

namespace N {
   struct C;

   namespace O {
      struct B;
   }

   // in N
   struct ::A {};   // C2911  A is member of global NS
   struct O::B{};   // OK B is in O, O is inside of N
   struct C {};     // OK C is member of N
   struct M::D {};  // C2911 D is member of M, M not enclosed by N
}
```