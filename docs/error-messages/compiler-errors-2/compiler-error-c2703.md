---
title: 編譯器錯誤 C2703
ms.date: 11/04/2016
f1_keywords:
- C2703
helpviewer_keywords:
- C2703
ms.assetid: 384295c3-643d-47ae-a9a6-865b3036aa84
ms.openlocfilehash: 62e03d1edc5806a9babc44eaf2dc388e3ed81de9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221103"
---
# <a name="compiler-error-c2703"></a>編譯器錯誤 C2703

不合法的 __leave 語句

* * `__leave** statement must be inside a ` __Try ' 區塊。

下列範例會產生 C2703：

```cpp
// C2703.cpp
int main() {
   __leave;   // C2703
   __try {
      // try the following line instead
      __leave;
   }
   __finally {}
}
```
