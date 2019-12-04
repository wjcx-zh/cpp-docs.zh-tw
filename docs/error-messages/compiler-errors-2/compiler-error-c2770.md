---
title: 編譯器錯誤 C2770
ms.date: 11/04/2016
f1_keywords:
- C2770
helpviewer_keywords:
- C2770
ms.assetid: 100001b5-80b0-4971-8ff6-9023f443c926
ms.openlocfilehash: 4f6c82823dc619982ff148a83e2cc3316b42cfab
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759772"
---
# <a name="compiler-error-c2770"></a>編譯器錯誤 C2770

' template ' 的明確 template_or_generic 引數無效

具有明確範本或泛型引數的函式樣板候選項目會產生不允許的函數類型。

下列範例會產生 C2770：

```cpp
// C2770.cpp
#include <stdio.h>
template <class T>
int f(typename T::B*);   // expects type with member B

struct Err {};

int main() {
   f<int>(0);   // C2770 int has no B
   // try the following line instead
   f<OK>(0);
}
```
