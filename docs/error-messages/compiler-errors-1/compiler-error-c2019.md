---
title: 編譯器錯誤 C2019 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2019
dev_langs:
- C++
helpviewer_keywords:
- C2019
ms.assetid: 4f37b1e1-9eca-418f-a4c3-141e8512d7b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e6f1ae1b22cca0d00e990f64ccaf469359563f8e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038694"
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