---
title: 編譯器錯誤 C2493
ms.date: 11/04/2016
f1_keywords:
- C2493
helpviewer_keywords:
- C2493
ms.assetid: 68316cd5-682b-49c3-b6ea-23c4e5d296cf
ms.openlocfilehash: e3c38167ff2b6d2b2f78a1357a9450a70cb421cc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216189"
---
# <a name="compiler-error-c2493"></a>編譯器錯誤 C2493

不合法的 __based 形式

**`__based`** 運算式必須以指標為基礎。

下列範例會產生 C2493：

```cpp
// C2493.cpp
// compile with: /c
char mybase;
int __based(mybase) ptr;   // C2493

// OK
char * mybase;
int __based(mybase) * ptr;
```
