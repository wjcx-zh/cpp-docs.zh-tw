---
title: 編譯器錯誤 C2883
ms.date: 11/04/2016
f1_keywords:
- C2883
helpviewer_keywords:
- C2883
ms.assetid: 5c6d689d-ed42-41ad-b5c0-e9c2e0b8c356
ms.openlocfilehash: 3f32307e519394433927d49aa92333fdff7b70f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587508"
---
# <a name="compiler-error-c2883"></a>編譯器錯誤 C2883

'name': 由 using 宣告引入 'identifier' 函式宣告衝突

您嘗試一次以上定義的函式。 從具有的命名空間進行的第一個定義`using`宣告。 第二個是本機的定義。

下列範例會產生 C2883:

```
// C2883.cpp
namespace A {
   void z(int);
}

int main() {
   using A::z;
   void z(int);   // C2883  z is already defined
}
```