---
title: 編譯器警告 （層級 1） C4003
ms.date: 11/04/2016
f1_keywords:
- C4003
helpviewer_keywords:
- C4003
ms.assetid: 0ed1c285-4428-4c90-8131-86897e31f115
ms.openlocfilehash: 7b1b87c643111f2b12124e348be8fb823e113937
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653150"
---
# <a name="compiler-warning-level-1-c4003"></a>編譯器警告 （層級 1） C4003

巨集 'identifier' 的實質參數不足

在巨集定義的型式參數的數目超過巨集中的實際參數數目。 巨集展開替代遺漏參數的空白文字。

下列範例會產生 C4003:

```
// C4003.cpp
// compile with: /WX
#define test(a,b) (a+b)

int main()
{
   int a = 1;
   int b = 2;
   a = test(b);   // C4003
   // try..
   a = test(a,b);
}
```