---
title: 編譯器錯誤 C2883
ms.date: 11/04/2016
f1_keywords:
- C2883
helpviewer_keywords:
- C2883
ms.assetid: 5c6d689d-ed42-41ad-b5c0-e9c2e0b8c356
ms.openlocfilehash: fcd97a2f362e50ec856e53da2603c29e07595670
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233466"
---
# <a name="compiler-error-c2883"></a>編譯器錯誤 C2883

' name '：函式宣告與使用-宣告引入的 ' identifier ' 衝突

您嘗試多次定義函式。 第一個定義是從具有宣告的命名空間進行 **`using`** 。 第二個是本機定義。

下列範例會產生 C2883：

```cpp
// C2883.cpp
namespace A {
   void z(int);
}

int main() {
   using A::z;
   void z(int);   // C2883  z is already defined
}
```
