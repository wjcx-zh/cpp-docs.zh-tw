---
title: 編譯器錯誤 C2034
ms.date: 11/04/2016
f1_keywords:
- C2034
helpviewer_keywords:
- C2034
ms.assetid: 953d70fa-bde9-4ce6-a55d-741e7bc63ff4
ms.openlocfilehash: 4b4fe769f78e5f826ba08d4819019210f21f860f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479673"
---
# <a name="compiler-error-c2034"></a>編譯器錯誤 C2034

'identifier': 位元欄位而言太小的位元數的型別

位元欄位宣告中的位元數超過基底類型的大小。

下列範例會產生 C2034:

```
// C2034.cpp
struct A {
   char test : 9;   // C2034, char has 8 bits
};
```

可能的解決方式：

```
// C2034b.cpp
// compile with: /c
struct A {
   char test : 8;
};
```