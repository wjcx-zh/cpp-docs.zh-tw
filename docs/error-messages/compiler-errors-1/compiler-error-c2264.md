---
title: 編譯器錯誤 C2264
ms.date: 11/04/2016
f1_keywords:
- C2264
helpviewer_keywords:
- C2264
ms.assetid: 158b72cc-cee9-4a08-bd79-b7a5955345a8
ms.openlocfilehash: df3b51c60a0546ed00a8cba7c6db066792cf50a2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758745"
---
# <a name="compiler-error-c2264"></a>編譯器錯誤 C2264

' function '：函式定義或宣告中有錯誤;未呼叫函式

因為定義或宣告不正確，所以無法呼叫函數。

下列範例會產生 C2264：

```cpp
// C2264.cpp
struct C {
   // Delete the following line to resolve.
   operator int(int = 0){}   // incorrect declaration
};

struct D {
   operator int(){return 0;}   // OK
};

int main() {
   int i;

   C c;
   i = c;   // C2264

   D d;
   i = d;   // OK
}
```
