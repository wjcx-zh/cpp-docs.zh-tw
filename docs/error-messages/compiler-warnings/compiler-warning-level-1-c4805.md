---
title: 編譯器警告 (層級 1) C4805
ms.date: 11/04/2016
f1_keywords:
- C4805
helpviewer_keywords:
- C4805
ms.assetid: 99c7b7e2-272e-4ab5-8580-17c42e62e2ef
ms.openlocfilehash: 129bff79b35fb14136cbf8127a3cfb77fc0d2a40
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051297"
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