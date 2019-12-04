---
title: 編譯器錯誤 C3354
ms.date: 11/04/2016
f1_keywords:
- C3354
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
ms.openlocfilehash: e5945b2112d1d03e4f18944d15028229cce4b668
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738592"
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

```cpp
// C3354_2.cpp
// compile with: /clr /c
using namespace System;
typedef void ( *VoidPfn )();

delegate VoidPfn func(); // C3354
// try the following line instead
// delegate  void func();
```
