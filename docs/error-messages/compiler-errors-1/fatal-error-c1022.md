---
title: 嚴重錯誤 C1022
ms.date: 11/04/2016
f1_keywords:
- C1022
helpviewer_keywords:
- C1022
ms.assetid: edada720-dc73-49bc-bd93-a7945a316312
ms.openlocfilehash: b709d4bd855e38cb3721dec6d09b95ed02454def
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756873"
---
# <a name="fatal-error-c1022"></a>嚴重錯誤 C1022

需要對應的 #endif

`#if`、 `#ifdef`或 `#ifndef` 指示詞沒有相符的 `#endif` 指示詞。 每個 `#if`、 `#ifdef`或 `#ifndef` 務必要有相符的 `#endif`。

下列範例會產生 C1022：

```cpp
// C1022.cpp
#define true 1

#if (true)
#else
#else    // C1022
```

可能的解決方案：

```cpp
// C1022b.cpp
// compile with: /c
#define true 1

#if (true)
#else
#endif
```
