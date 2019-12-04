---
title: 編譯器錯誤 C3828
ms.date: 11/04/2016
f1_keywords:
- C3828
helpviewer_keywords:
- C3828
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
ms.openlocfilehash: 4b47ddbf0775cab2bd7214f68d1b4ed6e06e6eea
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741699"
---
# <a name="compiler-error-c3828"></a>編譯器錯誤 C3828

' object type '：建立 managed 或 WinRTclasses 的實例時，不允許使用位置引數

建立 managed 類型的物件或 Windows 執行階段類型時，您無法使用運算子[ref new、gcnew](../../extensions/ref-new-gcnew-cpp-component-extensions.md)或[new](../../cpp/new-operator-cpp.md)的放置形式。

下列範例會產生 C3828，並示範如何修正此問題：

```cpp
// C3828a.cpp
// compile with: /clr
ref struct M {
};

ref struct N {
   static array<char>^ bytes = gcnew array<char>(256);
};

int main() {
   M ^m1 = new (&N::bytes) M();   // C3828
   // The following line fixes the error.
   // M ^m1 = gcnew M();
}
```
