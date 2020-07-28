---
title: 編譯器警告 (層級 3) C4646
ms.date: 11/04/2016
f1_keywords:
- C4646
helpviewer_keywords:
- C4646
ms.assetid: 23677e8e-603e-40e0-b99a-2e4894a1278e
ms.openlocfilehash: 3bbb9214a67284876c55e04485cea796cf9dbc29
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214421"
---
# <a name="compiler-warning-level-3-c4646"></a>編譯器警告 (層級 3) C4646

使用 __declspec(noreturn) 宣告的函式有非 void 的傳回類型

以[noreturn](../../cpp/noreturn.md)修飾詞標記的函式 **`__declspec`** 應該有[void](../../cpp/void-cpp.md)傳回類型。

下列範例會產生 C4646：

```cpp
// C4646.cpp
// compile with: /W3 /WX
int __declspec(noreturn) TestFunction()
{   // C4646  make return type void
}
```
