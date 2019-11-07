---
title: 編譯器警告（層級1） C4090
ms.date: 11/04/2016
f1_keywords:
- C4090
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
ms.openlocfilehash: 88ed48e9bf7057c55ee4004ca1bb1eb18cd4be51
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626157"
---
# <a name="compiler-warning-level-1-c4090"></a>編譯器警告（層級1） C4090

' operation '：不同的 ' 修飾詞 ' 限定詞

作業中使用的變數是使用指定的修飾詞所定義，以防止編譯器進行修改，而不會偵測到它。 運算式是在不修改的情況下編譯。

當**const**或 `volatile` 專案的指標指派給未宣告為指向**const**或 `volatile`的指標時，可能會產生這個警告。

C 程式會發出此警告。 在C++程式中，編譯器會發出錯誤： [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md)。

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