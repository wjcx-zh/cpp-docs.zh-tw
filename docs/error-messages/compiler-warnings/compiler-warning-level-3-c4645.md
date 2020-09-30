---
title: 編譯器警告 (層級 3) C4645
ms.date: 11/04/2016
f1_keywords:
- C4645
helpviewer_keywords:
- C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
ms.openlocfilehash: 246eed6592b892c3bd233d9217e26e7bf7a49ff8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502305"
---
# <a name="compiler-warning-level-3-c4645"></a>編譯器警告 (層級 3) C4645

使用 __declspec(noreturn) 宣告的函式有傳回的陳述式

在以 noreturn 修飾詞標記的函式中找到[return](../../cpp/program-termination.md)語句[noreturn](../../cpp/noreturn.md) **`__declspec`** 。 **`return`** 已忽略語句。

下列範例會產生 C4645：

```cpp
// C4645.cpp
// compile with:  /W3
void __declspec(noreturn) func() {
   return;   // C4645, delete this line to resolve
}

int main() {
}
```
