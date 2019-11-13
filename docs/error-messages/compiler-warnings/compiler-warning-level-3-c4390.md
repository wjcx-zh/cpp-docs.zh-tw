---
title: 編譯器警告（層級3） C4390
ms.date: 11/04/2016
f1_keywords:
- C4390
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
ms.openlocfilehash: 8402c6a2d0fcbb4704b833ac7ae2b070c7af3a48
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051596"
---
# <a name="compiler-warning-level-3-c4390"></a>編譯器警告（層級3） C4390

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