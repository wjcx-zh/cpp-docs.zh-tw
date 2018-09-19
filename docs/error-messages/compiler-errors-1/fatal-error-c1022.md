---
title: 嚴重錯誤 C1022 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1022
dev_langs:
- C++
helpviewer_keywords:
- C1022
ms.assetid: edada720-dc73-49bc-bd93-a7945a316312
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ddeea660515ea0a71e4807a34d2172413796046
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036731"
---
# <a name="fatal-error-c1022"></a>嚴重錯誤 C1022

需要對應的 #endif

`#if`、 `#ifdef`或 `#ifndef` 指示詞沒有相符的 `#endif` 指示詞。 每個 `#if`、 `#ifdef`或 `#ifndef` 務必要有相符的 `#endif`。

下列範例會產生 C1022：

```
// C1022.cpp
#define true 1

#if (true)
#else
#else    // C1022
```

可能的解決方式：

```
// C1022b.cpp
// compile with: /c
#define true 1

#if (true)
#else
#endif
```