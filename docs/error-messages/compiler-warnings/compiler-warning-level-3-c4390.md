---
title: 編譯器警告 (層級 3) C4390
ms.date: 11/04/2016
f1_keywords:
- C4390
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
ms.openlocfilehash: 4ca00f892adc8fe3ac1bffb59a27ea1744249dea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401978"
---
# <a name="compiler-warning-level-3-c4390"></a>編譯器警告 (層級 3) C4390

';': 控制找到空白陳述式;這是目的嗎？

找不到不包含任何指令的控制陳述式之後的分號。

如果您收到 C4390 由於巨集時，您應該使用[警告](../../preprocessor/warning.md)pragma 來停用 C4390，在模組中包含巨集。

下列範例會產生 C4390:

```
// C4390.cpp
// compile with: /W3
int main() {
   int i = 0;
   if (i);   // C4390
      i++;
}
```