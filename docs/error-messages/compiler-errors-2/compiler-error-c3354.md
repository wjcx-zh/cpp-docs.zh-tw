---
title: 編譯器錯誤 C3354 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3354
dev_langs:
- C++
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40f86702be19259bed7899cdbc5106346d6c6594
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058532"
---
# <a name="compiler-error-c3354"></a>編譯器錯誤 C3354

'function': 用來建立委派的函式不可以擁有傳回類型 'type'

下列類型作為 `delegate`的傳回類型時無效：

- 函式的指標

- 成員的指標

- 成員函式的指標

- 函式的參考

- 成員函式的參考

下列範例會產生 C3354：

```
// C3354_2.cpp
// compile with: /clr /c
using namespace System;
typedef void ( *VoidPfn )();

delegate VoidPfn func(); // C3354
// try the following line instead
// delegate  void func();
```
