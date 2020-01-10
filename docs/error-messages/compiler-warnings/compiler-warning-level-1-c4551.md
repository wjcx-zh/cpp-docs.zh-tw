---
title: 編譯器警告（層級1） C4551
ms.date: 11/04/2016
f1_keywords:
- C4551
helpviewer_keywords:
- C4551
ms.assetid: 458b59bd-e2d7-425f-9ba6-268ff200424f
ms.openlocfilehash: d4e7467efa8308e1044e8b7a166174c173dab166
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966371"
---
# <a name="compiler-warning-level-1-c4551"></a>編譯器警告（層級1） C4551

函式呼叫遺漏引數清單

函式呼叫必須在函式名稱後面加上左和右括弧，即使函式不接受任何參數也一樣。

下列範例會產生 C4551：

```cpp
// C4551.cpp
// compile with: /W1
void function1() {
}

int main() {
   function1;   // C4551
   function1();   // OK
}
```