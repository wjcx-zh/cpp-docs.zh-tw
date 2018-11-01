---
title: 編譯器錯誤 C2493
ms.date: 11/04/2016
f1_keywords:
- C2493
helpviewer_keywords:
- C2493
ms.assetid: 68316cd5-682b-49c3-b6ea-23c4e5d296cf
ms.openlocfilehash: d5e64b2586803f7463582710721d2cb5c0eac200
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443000"
---
# <a name="compiler-error-c2493"></a>編譯器錯誤 C2493

不合法的 __based 形式

A`__based`運算式必須以指標為基礎。

下列範例會產生 C2493:

```
// C2493.cpp
// compile with: /c
char mybase;
int __based(mybase) ptr;   // C2493

// OK
char * mybase;
int __based(mybase) * ptr;
```