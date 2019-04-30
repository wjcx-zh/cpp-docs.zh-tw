---
title: 編譯器警告 (層級 3) C4357
ms.date: 11/04/2016
f1_keywords:
- C4357
helpviewer_keywords:
- C4357
ms.assetid: 9259c633-3c02-4900-b94a-2d8d366d61cd
ms.openlocfilehash: a7923fdcda2a781c9680f8b3753fd101c73be19c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402017"
---
# <a name="compiler-warning-level-3-c4357"></a>編譯器警告 (層級 3) C4357

param 陣列引數的型式引數清單中委派 'del' 略過產生 'function' 時

`ParamArray`屬性會被忽略，和`function`無法呼叫具有變數引數。

下列範例會產生 C4357:

```
// C4357.cpp
// compile with: /clr /W3 /c
using namespace System;
public delegate void f(int i, ... array<Object^>^ varargs);   // C4357

public delegate void g(int i, array<Object^>^ varargs);   // OK
```