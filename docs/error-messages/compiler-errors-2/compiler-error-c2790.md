---
title: 編譯器錯誤 C2790
ms.date: 11/04/2016
f1_keywords:
- C2790
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
ms.openlocfilehash: c63fe7bb3686692818337e890de7fe4c80a18158
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739554"
---
# <a name="compiler-error-c2790"></a>編譯器錯誤 C2790

' super '：這個關鍵字只能用在類別成員函式的主體內

如果使用者曾嘗試在成員函式的內容之外使用關鍵字[super](../../cpp/super.md) ，就會出現這個錯誤訊息。

下列範例會產生 C2790：

```cpp
// C2790.cpp
void f() {
   __super::g();   // C2790
}
```
