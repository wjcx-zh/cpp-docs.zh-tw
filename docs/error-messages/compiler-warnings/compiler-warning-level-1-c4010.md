---
title: 編譯器警告 （層級 1） C4010
ms.date: 11/04/2016
f1_keywords:
- C4010
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
ms.openlocfilehash: 40c6724daf17c1c0b546bb7bc64bb704f732e8d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441245"
---
# <a name="compiler-warning-level-1-c4010"></a>編譯器警告 （層級 1） C4010

單行註解包含行接續字元

單行註解，導入的 / /，您也可以包含反斜線 (\\) 做為行接續字元。 編譯器會考慮要接續下一行，並將它視為註解。

部分語法導向編輯器並不表示成註解的接續字元的下一行。 忽略任何會導致此警告的行著色的語法。

下列範例會產生 C4010:

```
// C4010.cpp
// compile with: /WX
int main() {
   // the next line is also a comment because of the backslash \
   int a = 3; // C4010
   a++;
}
```