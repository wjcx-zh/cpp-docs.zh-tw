---
title: 編譯器警告（層級1） C4090
ms.date: 11/04/2016
f1_keywords:
- C4090
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
ms.openlocfilehash: c4cb71355b4f3dca66c56ed4b89012ca9b9e646d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197042"
---
# <a name="compiler-warning-level-1-c4090"></a>編譯器警告（層級1） C4090

' operation '：不同的 ' 修飾詞 ' 限定詞

作業中使用的變數是使用指定的修飾詞所定義，以防止編譯器進行修改，而不會偵測到它。 運算式是在不修改的情況下編譯。

當 **`const`** 或專案的指標 **`volatile`** 指派給未宣告為指向或的指標時，可能會造成這個警告 **`const`** **`volatile`** 。

C 程式會發出此警告。 在 c + + 程式中，編譯器會發出錯誤： [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md)。

下列範例會產生 C4090：

```c
// C4090.c
// compile with: /W1
int *volatile *p;
int *const *q;
int **r;

int main() {
   p = q;   // C4090
   p = r;
   q = p;   // C4090
   q = r;
   r = p;   // C4090
   r = q;   // C4090
}
```
