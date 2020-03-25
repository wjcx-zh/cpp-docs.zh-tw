---
title: 編譯器警告（層級1） C4003
ms.date: 11/04/2016
f1_keywords:
- C4003
helpviewer_keywords:
- C4003
ms.assetid: 0ed1c285-4428-4c90-8131-86897e31f115
ms.openlocfilehash: 3bf1eea1b8ad0529d6603a2388e61b9107304f43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164738"
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
