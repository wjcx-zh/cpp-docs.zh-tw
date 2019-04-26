---
title: 編譯器錯誤 C2267
ms.date: 11/04/2016
f1_keywords:
- C2267
helpviewer_keywords:
- C2267
ms.assetid: ea63bebb-6208-4367-8440-39be07f9c360
ms.openlocfilehash: 5ff8b0bee1f79d9534841e4368fd5a5249cbb413
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153394"
---
# <a name="compiler-error-c2267"></a>編譯器錯誤 C2267

'function': 具有區塊範圍的靜態函式不合法

區域函式宣告`static`。 靜態函式必須具有全域範圍。

下列範例會產生 C2267:

```
// C2267.cpp
static int func2();   // OK
int main() {
    static int func1();   // C2267
}
```