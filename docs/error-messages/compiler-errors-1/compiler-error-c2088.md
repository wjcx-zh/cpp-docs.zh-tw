---
title: 編譯器錯誤 C2088
ms.date: 11/04/2016
f1_keywords:
- C2088
helpviewer_keywords:
- C2088
ms.assetid: b93f7094-185b-423d-8bb9-507cd757dbf5
ms.openlocfilehash: 1f798774a7735a6aceb0bf75b3c6da9ccb1e4a72
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301973"
---
# <a name="compiler-error-c2088"></a>編譯器錯誤 C2088

' operator '：對 ' class-key ' 而言不合法

未定義結構或聯集的運算子。 此錯誤僅對 C 程式碼有效。

下列範例會產生 C2088 三次：

```c
// C2088.c
struct S {
   int m_i;
} s;

int main() {
   int i = s * 1;   // C2088
   struct S s2 = +s;   // C2088
   s++;   // C2088
}
```
