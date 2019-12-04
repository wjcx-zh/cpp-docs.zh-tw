---
title: 編譯器錯誤 C2267
ms.date: 11/04/2016
f1_keywords:
- C2267
helpviewer_keywords:
- C2267
ms.assetid: ea63bebb-6208-4367-8440-39be07f9c360
ms.openlocfilehash: c897f8e6b38743ee98ec29707b222901ddde9d7c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758732"
---
# <a name="compiler-error-c2267"></a>編譯器錯誤 C2267

' function '：具有區塊範圍的靜態函式不合法

`static`宣告區域函式。 靜態函式必須具有全域範圍。

下列範例會產生 C2267：

```cpp
// C2267.cpp
static int func2();   // OK
int main() {
    static int func1();   // C2267
}
```
