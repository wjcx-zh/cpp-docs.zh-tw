---
title: 編譯器錯誤 C2106
ms.date: 11/04/2016
f1_keywords:
- C2106
helpviewer_keywords:
- C2106
ms.assetid: d5c91a2e-04e4-4770-8478-788b98c52a53
ms.openlocfilehash: 6a82792c8a8acfd0d397e02929a457aae8ef7050
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507565"
---
# <a name="compiler-error-c2106"></a>編譯器錯誤 C2106

'operator': 左的運算元必須是左值

運算子必須為左運算元是左值。

下列範例會產生 C2106:

```
// C2106.cpp
int main() {
   int a;
   1 = a;   // C2106
   a = 1;   // OK
}
```