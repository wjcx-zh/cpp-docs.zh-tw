---
title: 編譯器警告 （層級 3） C4390 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4390
dev_langs:
- C++
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83131119e360bcf8193c2d6c8ca5a3cd09341516
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054183"
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