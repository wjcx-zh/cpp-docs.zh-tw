---
title: 編譯器警告 (層級 1) C4805
ms.date: 11/04/2016
f1_keywords:
- C4805
helpviewer_keywords:
- C4805
ms.assetid: 99c7b7e2-272e-4ab5-8580-17c42e62e2ef
ms.openlocfilehash: c724af59b0654ae0f212eea038c48cb57f991aa3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175060"
---
# <a name="compiler-warning-level-1-c4805"></a>編譯器警告 (層級 1) C4805

'operation'：作業中不安全的混用類型 'type' 和類型 'type'

針對[bool](../../cpp/bool-cpp.md)和[int](../../c-language/integer-types.md)之間的比較作業，會產生這個警告。下列範例會產生 C4805：

```cpp
// C4805.cpp
// compile with: /W1
int main() {
   int i = 1;
   bool b = true;

   if (i == b) {   // C4805, comparing bool and int variables
   }
}
```
