---
title: 編譯器警告 （層級 3） C4197
ms.date: 11/04/2016
f1_keywords:
- C4197
helpviewer_keywords:
- C4197
ms.assetid: f766feef-82b0-4d81-8a65-33628c7db196
ms.openlocfilehash: 15b2fba94bfc956775a1e454893e7509a32000e5
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522619"
---
# <a name="compiler-warning-level-3-c4197"></a>編譯器警告 （層級 3） C4197

'type': 轉換中最上層的 volatile 會被忽略

編譯器偵測到的轉型為右值型別這來限定[volatile](../../cpp/volatile-cpp.md)，或 volatile 限定某種類型的右值類型的轉換。 C 標準 (6.5.3)，根據限定的型別相關聯的屬性是僅對左值運算式有意義的。

下列範例會產生 C4197:

```
// C4197.cpp
// compile with: /W3
#include <stdio.h>
#include <signal.h>
#include <stdlib.h>

void sigproc(int);
struct S
{
   int i;
} s;

int main()
{
   signal(SIGINT, sigproc);
   s.i = 1;
   S *pS = &s;
   for ( ; (volatile int)pS->i ; )   // C4197
      break;
   // for ( ; *(volatile int *)&pS->i ; )   // OK
   //    break;
}

void sigproc(int) // ctrl-C
{
   signal(SIGINT, sigproc);
   s.i = 0;
}
```