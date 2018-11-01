---
title: 編譯器警告 (層級 1) C4805
ms.date: 11/04/2016
f1_keywords:
- C4805
helpviewer_keywords:
- C4805
ms.assetid: 99c7b7e2-272e-4ab5-8580-17c42e62e2ef
ms.openlocfilehash: 3bbce2529b208b764fa28bad1d67e1bbb38ec127
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662744"
---
# <a name="compiler-warning-level-1-c4805"></a>編譯器警告 (層級 1) C4805

'operation'：作業中不安全的混用類型 'type' 和類型 'type'

進行 [bool](../../cpp/bool-cpp.md) 和 [int](../../c-language/integer-types.md)之間的比較作業時會產生此警告。下列範例會產生 C4805：

```
// C4805.cpp
// compile with: /W1
int main() {
   int i = 1;
   bool b = true;

   if (i == b) {   // C4805, comparing bool and int variables
   }
}
```