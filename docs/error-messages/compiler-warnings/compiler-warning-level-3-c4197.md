---
title: 編譯器警告 （層級 3） C4197 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4197
dev_langs:
- C++
helpviewer_keywords:
- C4197
ms.assetid: f766feef-82b0-4d81-8a65-33628c7db196
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e3651a305b8654b9d7d36238885233b8e583f27
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043608"
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