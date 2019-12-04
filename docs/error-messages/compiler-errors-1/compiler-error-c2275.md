---
title: 編譯器錯誤 C2275
ms.date: 11/04/2016
f1_keywords:
- C2275
helpviewer_keywords:
- C2275
ms.assetid: c1eafa71-48de-46e0-82f3-b575538ef205
ms.openlocfilehash: 3e929adaf90c32cd489975057791a2866b6ba3e0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759733"
---
# <a name="compiler-error-c2275"></a>編譯器錯誤 C2275

' identifier '：使用此類型做為運算式的方式不合法

運算式會使用 `->` 運算子搭配 `typedef` 識別碼。

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
