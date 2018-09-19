---
title: 編譯器警告 （層級 1） C4805 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4805
dev_langs:
- C++
helpviewer_keywords:
- C4805
ms.assetid: 99c7b7e2-272e-4ab5-8580-17c42e62e2ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1fa9352dbd4138a755c603d332ff79232d7bb72a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103447"
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