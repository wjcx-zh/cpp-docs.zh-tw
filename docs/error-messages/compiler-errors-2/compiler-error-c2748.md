---
title: 編譯器錯誤 C2748
ms.date: 11/04/2016
f1_keywords:
- C2748
helpviewer_keywords:
- C2748
ms.assetid: b63ac78b-a200-499c-afea-15af1a1e819e
ms.openlocfilehash: 251492b736ba3325ed263a9a8754fc8fa480c664
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360225"
---
# <a name="compiler-error-c2748"></a>編譯器錯誤 C2748

Managed 或 WinRT 陣列建立必須有陣列大小或陣列初始設定式

Managed 或 WinRT 陣列格式錯誤。 如需詳細資訊，請參閱 [陣列](../../extensions/arrays-cpp-component-extensions.md)。

下列範例會產生 C2748，並示範如何修正此問題：

```
// C2748.cpp
// compile with: /clr
int main() {
   array<int> ^p1 = new array<int>();   // C2748
   // try the following line instead
   array<int> ^p2 = new array<int>(2);
}
```