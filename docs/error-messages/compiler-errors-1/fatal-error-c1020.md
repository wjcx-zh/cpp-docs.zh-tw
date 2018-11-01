---
title: 嚴重錯誤 C1020
ms.date: 11/04/2016
f1_keywords:
- C1020
helpviewer_keywords:
- C1020
ms.assetid: 42f429e2-5e3b-4086-a10d-b99e032e51c5
ms.openlocfilehash: bdd7a6c87b0e00bd7bef174b8daf0e16cc488a5d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469806"
---
# <a name="fatal-error-c1020"></a>嚴重錯誤 C1020

未預期的 #endif

`#endif` 指示詞沒有對應的 `#if`、 `#ifdef`或 `#ifndef` 指示詞。 每個 `#endif` 都一定要有對應的指示詞。

下列範例會產生 C1020：

```
// C1020.cpp
#endif     // C1020
```

可能的解決方式：

```
// C1020b.cpp
// compile with: /c
#if 1
#endif
```