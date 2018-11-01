---
title: 編譯器警告 （層級 1） C4090
ms.date: 11/04/2016
f1_keywords:
- C4090
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
ms.openlocfilehash: b47d0bfbb6eab24fbe811d3e4f79b6bd86b3bb11
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462370"
---
# <a name="compiler-warning-level-1-c4090"></a>編譯器警告 （層級 1） C4090

'operation': 不同的 'modifier' 限定詞

使用指定的修飾詞，所以無法由編譯器不需要偵測正在修改定義作業所使用的變數。 運算式會編譯而不需修改。

指標時，可能造成這項警告**const**或是`volatile`項目指派給未宣告為指向指標**const**或`volatile`。

C 程式會發出這個警告。 在 c + + 程式中，編譯器會發出錯誤： [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md)。

下列範例會產生 C4090:

```
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