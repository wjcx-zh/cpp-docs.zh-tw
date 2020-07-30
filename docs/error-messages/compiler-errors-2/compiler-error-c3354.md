---
title: 編譯器錯誤 C3354
ms.date: 11/04/2016
f1_keywords:
- C3354
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
ms.openlocfilehash: fdc5de7493decf1f44617ab22a00fb5e8852116f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231971"
---
# <a name="compiler-error-c3354"></a>編譯器錯誤 C3354

'function': 用來建立委派的函式不可以擁有傳回類型 'type'

下列類型無效，做為的傳回類型 **`delegate`** ：

- 函式的指標

- 成員的指標

- 成員函式的指標

- 函式的參考

- 成員函式的參考

下列範例會產生 C3354：

```cpp
// C3354_2.cpp
// compile with: /clr /c
using namespace System;
typedef void ( *VoidPfn )();

delegate VoidPfn func(); // C3354
// try the following line instead
// delegate  void func();
```
