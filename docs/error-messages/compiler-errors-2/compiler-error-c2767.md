---
title: 編譯器錯誤 C2767
ms.date: 11/04/2016
f1_keywords:
- C2767
helpviewer_keywords:
- C2767
ms.assetid: e8f84178-a160-4d71-a236-07e4fcc11e96
ms.openlocfilehash: 6c13610b6fd7aae4b4232b836a0307867bd591d7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550146"
---
# <a name="compiler-error-c2767"></a>編譯器錯誤 C2767

受管理或 WinRTarray 維度不相符： 預期 N 引數-提供 M

Managed 或 WinRT 陣列宣告的格式錯誤。 如需詳細資訊，請參閱 [陣列](../../windows/arrays-cpp-component-extensions.md)。

下列範例會產生 C2767，並說明如何加以修正：

```
// C2767.cpp
// compile with: /clr
int main() {
   array<int> ^p1 = new array<int>(2,3); // C2767
   array<int> ^p2 = new array<int>(2);   // OK
}
```