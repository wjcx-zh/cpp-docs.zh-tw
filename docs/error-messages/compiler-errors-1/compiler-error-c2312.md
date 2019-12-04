---
title: 編譯器錯誤 C2312
ms.date: 11/04/2016
f1_keywords:
- C2312
helpviewer_keywords:
- C2312
ms.assetid: c8bcfd06-12c1-4323-bb53-ba392d36daa4
ms.openlocfilehash: 0a0fbefcb1122e5c3395580a2508420b1ccea17c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748134"
---
# <a name="compiler-error-c2312"></a>編譯器錯誤 C2312

'exception1': 是 'exception2' 在行號攔截到

兩個處理常式會捕捉相同的例外狀況類型。

下列範例會產生 C2312：

```cpp
// C2312.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
    try {
        throw "ooops!";
    }
    catch( signed int ) {}
    catch( int ) {}   // C2312
}
```
