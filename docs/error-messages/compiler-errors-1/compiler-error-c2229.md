---
title: 編譯器錯誤 C2229
ms.date: 11/04/2016
f1_keywords:
- C2229
helpviewer_keywords:
- C2229
ms.assetid: 933c7cf2-a463-4e74-b0b4-59dedad987fb
ms.openlocfilehash: 998067e9af178c1898c3443c4e84da965c22fa81
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301730"
---
# <a name="compiler-error-c2229"></a>編譯器錯誤 C2229

類型 'identifier' 有不合法的大小為零的陣列

結構或位元欄位成員包含不是最後一個成員的大小為零的陣列。

因為您可以為零大小的陣列做為結構的最後一個成員，您必須指定其大小，當您配置結構。

如果為零大小的陣列不是結構的最後一個成員，編譯器就無法計算其餘欄位的位移。

下列範例會產生 C2229:

```
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