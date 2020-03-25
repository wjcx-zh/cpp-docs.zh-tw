---
title: 編譯器警告（層級3） C4197
ms.date: 11/04/2016
f1_keywords:
- C4197
helpviewer_keywords:
- C4197
ms.assetid: f766feef-82b0-4d81-8a65-33628c7db196
ms.openlocfilehash: fbc3fbf7f7408f854b1de969688dfbd25e826d84
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161590"
---
# <a name="compiler-warning-level-3-c4197"></a>編譯器警告（層級3） C4197

' type '：已忽略 cast 中的最上層 volatile

編譯器偵測到轉換成以[volatile](../../cpp/volatile-cpp.md)限定的 r 值型別，或將 r 值型別轉換成以 volatile 限定的某種型別。 根據 C 標準（6.5.3），與限定型別相關聯的屬性只對左值運算式有意義。

下列範例會產生 C4197：

```cpp
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
