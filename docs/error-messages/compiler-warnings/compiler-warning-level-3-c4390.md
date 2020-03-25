---
title: 編譯器警告 (層級 3) C4390
ms.date: 11/04/2016
f1_keywords:
- C4390
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
ms.openlocfilehash: 63150f4ca801d3c377c7bc09b58a778bebf02b46
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198675"
---
# <a name="compiler-warning-level-3-c4390"></a>編譯器警告 (層級 3) C4390

'; '：找到空的受控制語句;這是意圖嗎？

在不含指示的控制項語句之後，找到分號。

如果您因為宏而取得 C4390，您應該使用[warning](../../preprocessor/warning.md) pragma 來停用包含宏之模組中的 C4390。

下列範例會產生 C4390：

```cpp
// C4390.cpp
// compile with: /W3
int main() {
   int i = 0;
   if (i);   // C4390
      i++;
}
```
