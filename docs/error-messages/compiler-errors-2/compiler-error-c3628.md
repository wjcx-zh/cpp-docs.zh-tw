---
title: 編譯器錯誤 C3628
ms.date: 11/04/2016
f1_keywords:
- C3628
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
ms.openlocfilehash: 9976cb2425f8f855ffb2903c07de22822c781e20
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755820"
---
# <a name="compiler-error-c3628"></a>編譯器錯誤 C3628

' base class '： managed 或 WinRTclasses 僅支援公用繼承

嘗試使用 managed 或 WinRT 類別做為[私](../../cpp/private-cpp.md)用或[受保護](../../cpp/protected-cpp.md)的基類。 Managed 或 WinRT 類別只能用來做為具有[公用](../../cpp/public-cpp.md)存取權的基類。

下列範例會產生 C3628，並顯示如何修正此問題：

```cpp
// C3628a.cpp
// compile with: /clr
ref class B {
};

ref class D : private B {   // C3628

// The following line resolves the error.
// ref class D : public B {
};

int main() {
}
```
