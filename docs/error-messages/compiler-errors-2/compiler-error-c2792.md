---
title: 編譯器錯誤 C2792
ms.date: 11/04/2016
f1_keywords:
- C2792
helpviewer_keywords:
- C2792
ms.assetid: 392cf748-4f5e-4e62-a364-3118d5658408
ms.openlocfilehash: 175ec7ff6b842eb5f41896c5ec3cc0a0f5db817c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739528"
---
# <a name="compiler-error-c2792"></a>編譯器錯誤 C2792

' super '：此關鍵字後面必須加上 '：： '

唯一可以遵循關鍵字 `__super` 的 token 是 `::`。

下列範例會產生 C2792：

```cpp
// C2792.cpp
struct B {
   void mf();
};

struct D : B {
   void mf() {
      __super.();   // C2792

      // try the following line instead
      // __super::mf();
   }
};
```
