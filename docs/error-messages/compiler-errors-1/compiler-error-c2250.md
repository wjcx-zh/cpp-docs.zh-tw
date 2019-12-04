---
title: 編譯器錯誤 C2250
ms.date: 11/04/2016
f1_keywords:
- C2250
helpviewer_keywords:
- C2250
ms.assetid: f990986f-5c7d-4af4-a25c-b35540f1e217
ms.openlocfilehash: 472aabf00fecd000f274d97b5753ed8460ff867f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758862"
---
# <a name="compiler-error-c2250"></a>編譯器錯誤 C2250

' identifier '： ' class：： member ' 的繼承不明確

衍生的類別會繼承虛擬基類虛擬函式的多個覆寫。 這些覆寫在衍生類別中是不明確的。

下列範例會產生 C2286：

```cpp
// C2250.cpp
// compile with: /c
// C2250 expected
struct V {
   virtual void vf();
};

struct A : virtual V {
   void vf();
};

struct B : virtual V {
   void vf();
};

struct D : A, B {
   // Uncomment the following line to resolve.
   // void vf();
};
```
