---
title: 編譯器錯誤 C2275
ms.date: 11/04/2016
f1_keywords:
- C2275
helpviewer_keywords:
- C2275
ms.assetid: c1eafa71-48de-46e0-82f3-b575538ef205
ms.openlocfilehash: debf8779014badab69ffca13f3795f7e004b292a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182778"
---
# <a name="compiler-error-c2275"></a>編譯器錯誤 C2275

'identifier': 不合法使用這個型別做為運算式

運算式會使用`->`運算子搭配`typedef`識別項。

下列範例會產生 C2275:

```
// C2275.cpp
typedef struct S {
    int mem;
} *S_t;
void func1( int *parm );
void func2() {
    func1( &S_t->mem );   // C2275, S_t is a typedef
}
```