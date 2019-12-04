---
title: 編譯器錯誤 C2767
ms.date: 11/04/2016
f1_keywords:
- C2767
helpviewer_keywords:
- C2767
ms.assetid: e8f84178-a160-4d71-a236-07e4fcc11e96
ms.openlocfilehash: 259e8a58abfa2dc5eacaa6c9f6e3d47b852f5c1f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759811"
---
# <a name="compiler-error-c2767"></a>編譯器錯誤 C2767

managed 或 WinRTarray 維度不相符：預期有 N 個引數-已提供 M 個

Managed 或 WinRT 陣列宣告的格式錯誤。 如需詳細資訊，請參閱 [陣列](../../extensions/arrays-cpp-component-extensions.md)。

下列範例會產生 C2767，並說明如何加以修正：

```cpp
// C2767.cpp
// compile with: /clr
int main() {
   array<int> ^p1 = new array<int>(2,3); // C2767
   array<int> ^p2 = new array<int>(2);   // OK
}
```
