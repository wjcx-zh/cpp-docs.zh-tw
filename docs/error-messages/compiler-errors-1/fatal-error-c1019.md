---
title: 嚴重錯誤 C1019
ms.date: 11/04/2016
f1_keywords:
- C1019
helpviewer_keywords:
- C1019
ms.assetid: c4f8968b-bc62-4200-b3ca-69d06c163236
ms.openlocfilehash: 2d8e63510b762b0de0cda50ab7a03b773dfb949a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383122"
---
# <a name="fatal-error-c1019"></a>嚴重錯誤 C1019

未預期的 #else

`#else` 指示詞出現在 `#if`、 `#ifdef`或 `#ifndef` 建構外部。 請僅在其中一個建構內使用 `#else` 。

下列範例會產生 C1019：

```
// C1019.cpp
#else   // C1019
#endif

int main() {}
```

可能的解決方式：

```
// C1019b.cpp
#if 1
#else
#endif

int main() {}
```