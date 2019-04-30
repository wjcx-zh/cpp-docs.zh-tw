---
title: 編譯器警告 （層級 3） C4018
ms.date: 11/04/2016
f1_keywords:
- C4018
helpviewer_keywords:
- C4018
ms.assetid: 6e8cbb04-d914-4319-b431-cbc2fbe40eb1
ms.openlocfilehash: 6436f62a06cbe931ca5b42751d60507f21675c5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402368"
---
# <a name="compiler-warning-level-3-c4018"></a>編譯器警告 （層級 3） C4018

'expression': signed/unsigned 不相符

比較的帶正負號和不帶正負號的數字需要編譯器將帶正負號的值轉換成不帶正負號。

如果您將轉換的兩種類型的其中一個測試帶正負號和不帶正負號類型時，可能會修正這個警告。

下列範例會產生 C4018:

```
// C4018.cpp
// compile with: /W3
int main() {
   unsigned int uc = 0;
   int c = 0;
   unsigned int c2 = 0;

   if (uc < c) uc = 0;   // C4018

   // OK
   if (uc == c2) uc = 0;
}
```