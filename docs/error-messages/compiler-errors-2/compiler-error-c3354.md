---
title: 編譯器錯誤 C3354
ms.date: 11/04/2016
f1_keywords:
- C3354
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
ms.openlocfilehash: 1ff2967f602722c99b58b679324bd4f50575f109
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523147"
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
