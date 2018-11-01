---
title: 編譯器錯誤 C2012
ms.date: 11/04/2016
f1_keywords:
- C2012
helpviewer_keywords:
- C2012
ms.assetid: 9f0d8162-c0b3-4234-a41f-836fdb75c84e
ms.openlocfilehash: 85c3ad1d127dcabeeed0c5727ba6bbbca86f7898
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499654"
---
# <a name="compiler-error-c2012"></a>編譯器錯誤 C2012

'<' 之後遺漏名稱

`#include` 指示詞缺少必要的檔名。

下列範例會產生 C2012：

```
// C2012.cpp
#include <   // C2012 include the filename to resolve
```

可能的解決方式：

```
// C2012b.cpp
// compile with: /c
#include <stdio.h>
```