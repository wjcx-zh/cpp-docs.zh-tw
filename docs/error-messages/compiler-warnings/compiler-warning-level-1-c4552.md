---
title: 編譯器警告 （層級 1） C4552 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4552
dev_langs:
- C++
helpviewer_keywords:
- C4552
ms.assetid: ebbbb5ee-1c19-45bd-b386-41a19630fc76
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62c08ea81f5f8794a1dd4ff7d0b5644e9a669e0f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048067"
---
# <a name="compiler-warning-level-1-c4552"></a>編譯器警告 (層級 1) C4552

'operator': 運算子沒有任何作用中;必須是具有副作用的運算子

如果運算式陳述式會有一個運算子，而沒有副作用，與運算式的上方，就可能發生錯誤。

若要覆寫這項警告，請將運算式放在括號中。

下列範例會產生 C4552:

```
// C4552.cpp
// compile with: /W1
int main() {
   int i, j;
   i + j;   // C4552
   // try the following line instead
   // (i + j);
}
```