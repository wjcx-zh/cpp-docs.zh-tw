---
title: 編譯器警告 （層級 1） C4090 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4090
dev_langs:
- C++
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ae34eeb6c87fdb12b07d25c6b6bbcfdd6b5ee21
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024803"
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