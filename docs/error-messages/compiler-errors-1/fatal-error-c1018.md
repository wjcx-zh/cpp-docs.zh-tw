---
title: 嚴重錯誤 C1018
ms.date: 11/04/2016
f1_keywords:
- C1018
helpviewer_keywords:
- C1018
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
ms.openlocfilehash: 327bc0d5200fc348611da107257f2086063648fa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383213"
---
# <a name="fatal-error-c1018"></a>嚴重錯誤 C1018

未預期的 #elif

`#elif` 指示詞出現在 `#if`、 `#ifdef`或 `#ifndef` 建構外部。 請僅在其中一個建構內使用 `#elif` 。

下列範例會產生 C1018：

```
// C1018.cpp
#elif      // C1018
#endif

int main() {}
```

可能的解決方式：

```
// C1018b.cpp
#if 1
#elif
#endif

int main() {}
```