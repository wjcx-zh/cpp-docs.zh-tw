---
title: 編譯器錯誤 C2234
ms.date: 11/04/2016
f1_keywords:
- C2234
helpviewer_keywords:
- C2234
ms.assetid: cfa42458-c803-4717-a017-9eca1c0cbfb0
ms.openlocfilehash: 16cc09f43f8705452c207e5218f4cc274557e825
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611467"
---
# <a name="compiler-error-c2234"></a>編譯器錯誤 C2234

'name': 參考的陣列不合法

因為不允許參考的指標，參考的陣列不可行。

下列範例會產生 C2234:

```
// C2234.cpp
int main() {
   int i = 0, j = 0, k = 0, l = 0;
   int &array[4] = {i,j,k,l};   // C2234
   int array2[4] = {i,j,k,l};   // OK
}
```