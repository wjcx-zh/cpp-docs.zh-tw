---
title: 編譯器錯誤 C2135
ms.date: 11/04/2016
f1_keywords:
- C2135
helpviewer_keywords:
- C2135
ms.assetid: aa360d22-4f79-4de1-b384-93cadd10975f
ms.openlocfilehash: 0b6cc8fb8ec1c6a7b054eb48d914335460811310
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344911"
---
# <a name="compiler-error-c2135"></a>編譯器錯誤 C2135

'bit operator': 不合法的位元欄位運算

傳址運算子 (`&`) 無法套用至位元欄位。

下列範例會產生 C2135：

```
// C2135.cpp
struct S {
   int i : 1;
};

struct T {
   int j;
};
int main() {
   &S::i;   // C2135 address of a bit field
   &T::j;   // OK
}
```