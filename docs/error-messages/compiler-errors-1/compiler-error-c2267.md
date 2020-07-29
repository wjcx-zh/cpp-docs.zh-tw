---
title: 編譯器錯誤 C2267
ms.date: 11/04/2016
f1_keywords:
- C2267
helpviewer_keywords:
- C2267
ms.assetid: ea63bebb-6208-4367-8440-39be07f9c360
ms.openlocfilehash: 0a72470feb79a226fe0f167364eeaea7dec9fd4d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87208469"
---
# <a name="compiler-error-c2267"></a>編譯器錯誤 C2267

' function '：具有區塊範圍的靜態函式不合法

已宣告區域函式 **`static`** 。 靜態函式必須具有全域範圍。

下列範例會產生 C2267：

```cpp
// C2267.cpp
static int func2();   // OK
int main() {
    static int func1();   // C2267
}
```
