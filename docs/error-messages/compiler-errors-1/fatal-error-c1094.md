---
title: 嚴重錯誤 C1094
ms.date: 11/04/2016
f1_keywords:
- C1094
helpviewer_keywords:
- C1094
ms.assetid: 9e1193b2-cb95-44f9-bf6f-019e0d41dd97
ms.openlocfilehash: 23891a783a018f6d84ea820af98992f61632984c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366494"
---
# <a name="fatal-error-c1094"></a>嚴重錯誤 C1094

'-Zmval1': 命令列選項不一致，用來建置先行編譯標頭的值 ('-Zmval2')

值傳遞給[/Yc](../../build/reference/yc-create-precompiled-header-file.md)必須是相同的值傳遞給[/Yu](../../build/reference/yu-use-precompiled-header-file.md) (**/Zm**值必須在所有編譯中使用，或建立相同的先行編譯的相同標頭檔）。

下列範例會產生 C1094:

```
// C1094.h
int func1();
```

然後，

```
// C1094.cpp
// compile with: /Yc"C1094.h" /Zm200
int u;
int main() {
   int sd = 32;
}
#include "C1094.h"
```

然後，

```
// C1094b.cpp
// compile with: /Yu"C1094.h" /Zm300 /c
#include "C1094.h"   // C1094 compile with /Zm200
void Test() {}
```