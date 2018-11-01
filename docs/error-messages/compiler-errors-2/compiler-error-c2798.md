---
title: 編譯器錯誤 C2798
ms.date: 11/04/2016
f1_keywords:
- C2798
helpviewer_keywords:
- C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
ms.openlocfilehash: f3e8f0ac260e49866d1c654f89d34bf57a8ffbc1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463048"
---
# <a name="compiler-error-c2798"></a>編譯器錯誤 C2798

'super::member' 模稜兩可

多重繼承的結構包含您參考具有成員[super](../../cpp/super.md)。 您可以透過下列方式修正錯誤：

- D.繼承清單中移除 B1 或 B2

- 變更 B1 B2 中的資料成員的名稱。

下列範例會產生 C2798:

```
// C2798.cpp
struct B1 {
   int i;
};

struct B2 {
   int i;
};

struct D : B1, B2 {
   void g() {
      __super::i = 4; // C2798
   }
};
```