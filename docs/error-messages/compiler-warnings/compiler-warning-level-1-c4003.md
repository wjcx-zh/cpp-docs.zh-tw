---
title: 編譯器警告（層級1） C4003
ms.date: 11/04/2016
f1_keywords:
- C4003
helpviewer_keywords:
- C4003
ms.assetid: 0ed1c285-4428-4c90-8131-86897e31f115
ms.openlocfilehash: 4adbffe3220060ee9d43f01cf94628f85d3991cc
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627391"
---
# <a name="compiler-warning-level-1-c4003"></a>編譯器警告（層級1） C4003

巨集 'identifier' 的實質參數不足

巨集定義中的正式參數數目超過宏中的實際參數數目。 宏展開會將空白文字取代為遺漏的參數。

下列範例會產生 C4003：

```cpp
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