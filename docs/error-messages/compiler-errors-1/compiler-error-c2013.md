---
title: 編譯器錯誤 C2013 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2013
dev_langs:
- C++
helpviewer_keywords:
- C2013
ms.assetid: 6b5c955c-53da-48ee-8533-64ef5b905173
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a849900f3d981de74702d972ad9f45b7f31e5619
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113353"
---
# <a name="compiler-error-c2013"></a>編譯器錯誤 C2013

遺漏 '>'

`#include` 指示詞缺少右角括弧。 加入右角括弧，以解決錯誤。

下列範例會產生 C2013：

```
// C2013.cpp
#include <stdio.h    // C2013
```

可能的解決方式：

```
// C2013b.cpp
// compile with: /c
#include <stdio.h>
```