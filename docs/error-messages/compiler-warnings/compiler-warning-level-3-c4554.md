---
title: 編譯器警告 (層級 3) C4554
ms.date: 11/04/2016
f1_keywords:
- C4554
helpviewer_keywords:
- C4554
ms.assetid: 55bb68f0-2e80-4330-8921-51083c4f8d53
ms.openlocfilehash: 78e0bf70b0e5f17a9803f3a1942c2a4022e1006d
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188885"
---
# <a name="compiler-warning-level-3-c4554"></a>編譯器警告 (層級 3) C4554

' operator '：檢查運算子優先順序找出可能的錯誤;使用括弧來澄清優先順序

下列範例會產生 C4554：

```cpp
// C4554.cpp
// compile with: /W3 /WX
int main() {
   int a = 0, b = 0, c = 0;
   a = a << b + c;   // C4554
   // probably intended (a << b) + c,
   // but will get a << (b + c)
}
```