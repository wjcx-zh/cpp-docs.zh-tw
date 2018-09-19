---
title: 嚴重錯誤 C1094 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1094
dev_langs:
- C++
helpviewer_keywords:
- C1094
ms.assetid: 9e1193b2-cb95-44f9-bf6f-019e0d41dd97
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 15e722c6a74490a5fbb26e4e367f7f1b4cbcc932
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109245"
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