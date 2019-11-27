---
title: 編譯器警告 (層級 3) C4645
ms.date: 11/04/2016
f1_keywords:
- C4645
helpviewer_keywords:
- C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
ms.openlocfilehash: 4fa286f177284c03e5067b4af56f4e606b073653
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189367"
---
# <a name="compiler-warning-level-3-c4645"></a>編譯器警告 (層級 3) C4645

使用 __declspec(noreturn) 宣告的函式有傳回的陳述式

在以[noreturn](../../cpp/noreturn.md) `__declspec` 修飾詞標記的函式中找到[return](../../cpp/return-statement-in-program-termination-cpp.md)語句。 已忽略 `return` 陳述式。

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