---
title: 編譯器錯誤 C2019
ms.date: 11/04/2016
f1_keywords:
- C2019
helpviewer_keywords:
- C2019
ms.assetid: 4f37b1e1-9eca-418f-a4c3-141e8512d7b6
ms.openlocfilehash: 6e9e5bbca5da13fdfd4727d3b19aa3656689ce96
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531829"
---
# <a name="compiler-error-c2019"></a>編譯器錯誤 C2019

必須是前置處理器指示詞，但找到 'character'

字元後面接著`#`正負號，但它並不是前置處理器指示詞的第一個字母。

下列範例會產生 C2019:

```
// C2019.cpp
#!define TRUE 1   // C2019
```

可能的解決方式：

```
// C2019b.cpp
// compile with: /c
#define TRUE 1
```