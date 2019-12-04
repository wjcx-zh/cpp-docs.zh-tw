---
title: 編譯器錯誤 C2229
ms.date: 11/04/2016
f1_keywords:
- C2229
helpviewer_keywords:
- C2229
ms.assetid: 933c7cf2-a463-4e74-b0b4-59dedad987fb
ms.openlocfilehash: 2d974c4f0630a592daad956448bf21cea21efb7c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759265"
---
# <a name="compiler-error-c2229"></a>編譯器錯誤 C2229

類型 ' identifier ' 有不合法大小的陣列

結構或位欄位的成員包含大小為零的陣列，而不是最後一個成員。

因為您可以將零大小的陣列做為結構的最後一個成員，所以您必須在配置結構時指定其大小。

如果大小為零的陣列不是結構的最後一個成員，則編譯器無法計算其餘欄位的位移。

下列範例會產生 C2229：

```cpp
// C2229.cpp
struct S {
   int a[0];  // C2229  zero-sized array
   int b[1];
};

struct S2 {
   int a;
   int b[0];
};

int main() {
   // allocate 7 elements for b field
   S2* s2 = (S2*)new int[sizeof(S2) + 7*sizeof(int)];
   s2->b[6] = 100;
}
```
