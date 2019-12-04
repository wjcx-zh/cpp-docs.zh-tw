---
title: 編譯器錯誤 C2798
ms.date: 11/04/2016
f1_keywords:
- C2798
helpviewer_keywords:
- C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
ms.openlocfilehash: 6eed1f1aad0783f9e1d5f4126847b54f6b7278e0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739196"
---
# <a name="compiler-error-c2798"></a>編譯器錯誤 C2798

' super：： member ' 不明確

多個繼承的結構包含您以[super](../../cpp/super.md)參考的成員。 您可以透過下列其中一種方式來修正錯誤：

- 從 D 的繼承清單中移除 B1 或 B2。

- 變更 B1 或 B2 中的資料成員名稱。

下列範例會產生 C2798：

```cpp
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
