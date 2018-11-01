---
title: 編譯器錯誤 C2909
ms.date: 11/04/2016
f1_keywords:
- C2909
helpviewer_keywords:
- C2909
ms.assetid: 1c9df8ae-925d-4002-a5f8-a71413c45f9e
ms.openlocfilehash: 7a777e87d8110ac16740346a8494f9501ce93b37
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668841"
---
# <a name="compiler-error-c2909"></a>編譯器錯誤 C2909

'identifier': 函式樣板的明確具現化必須有傳回類型

函式樣板的明確具現化必須有其傳回類型的明確規格。 隱含傳回類型規格不適用。

下列範例會產生 C2909：

```
// C2909.cpp
// compile with: /c
template<class T> int f(T);
template f<int>(int);         // C2909
template int f<int>(int);   // OK
```