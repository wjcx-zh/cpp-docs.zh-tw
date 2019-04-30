---
title: 嚴重錯誤 C1022
ms.date: 11/04/2016
f1_keywords:
- C1022
helpviewer_keywords:
- C1022
ms.assetid: edada720-dc73-49bc-bd93-a7945a316312
ms.openlocfilehash: 044ebbbe895677acf74977e56879c292486e18cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383135"
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