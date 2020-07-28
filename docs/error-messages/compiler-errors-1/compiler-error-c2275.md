---
title: 編譯器錯誤 C2275
ms.date: 11/04/2016
f1_keywords:
- C2275
helpviewer_keywords:
- C2275
ms.assetid: c1eafa71-48de-46e0-82f3-b575538ef205
ms.openlocfilehash: f9ab2e16992333aed914f2f68967f75cb01e8bd9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220362"
---
# <a name="compiler-error-c2275"></a>編譯器錯誤 C2275

' identifier '：使用此類型做為運算式的方式不合法

運算式會搭配使用 `->` 運算子與 **`typedef`** 識別碼。

下列範例會產生 C2275：

```cpp
// C2275.cpp
typedef struct S {
    int mem;
} *S_t;
void func1( int *parm );
void func2() {
    func1( &S_t->mem );   // C2275, S_t is a typedef
}
```
