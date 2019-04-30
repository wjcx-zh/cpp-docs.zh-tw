---
title: 編譯器警告 (層級 1) C4163
ms.date: 11/04/2016
f1_keywords:
- C4163
helpviewer_keywords:
- C4163
ms.assetid: b08413fd-03fc-4f41-9167-a98976ac12f2
ms.openlocfilehash: 737cf7ad00bfefd429792eed3f730844789e0c02
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391760"
---
# <a name="compiler-warning-level-1-c4163"></a>編譯器警告 (層級 1) C4163

'identifier' : 無法當做內建函式使用

指定的函式不能用作為 [內建](../../preprocessor/intrinsic.md) 函式。 編譯器會忽略無效的函式名稱。

下列範例會產生 C4163：

```
// C4163.cpp
// compile with: /W1 /LD
#include <math.h>
#pragma intrinsic(mysin)   // C4163
// try the following line instead
// #pragma intrinsic(sin)
```