---
title: 嚴重錯誤 C1094
ms.date: 11/04/2016
f1_keywords:
- C1094
helpviewer_keywords:
- C1094
ms.assetid: 9e1193b2-cb95-44f9-bf6f-019e0d41dd97
ms.openlocfilehash: 99bfeea47ff46b6dadac9b32fa61306d54520d0f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747393"
---
# <a name="fatal-error-c1094"></a>嚴重錯誤 C1094

'-Zmval1 '：命令列選項與用來建立先行編譯標頭檔（'-Zmval2 '）的值不一致

傳遞給[/yc](../../build/reference/yc-create-precompiled-header-file.md)的值必須與傳遞給[/yu](../../build/reference/yu-use-precompiled-header-file.md)的值相同（使用或建立相同先行編譯標頭檔的所有編譯中的 **/zm**值必須相同）。

下列範例會產生 C1094：

```
// C1094.h
int func1();
```

然後，

```cpp
// C1094.cpp
// compile with: /Yc"C1094.h" /Zm200
int u;
int main() {
   int sd = 32;
}
#include "C1094.h"
```

然後，

```cpp
// C1094b.cpp
// compile with: /Yu"C1094.h" /Zm300 /c
#include "C1094.h"   // C1094 compile with /Zm200
void Test() {}
```
