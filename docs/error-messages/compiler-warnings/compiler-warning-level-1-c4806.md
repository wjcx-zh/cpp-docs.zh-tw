---
title: 編譯器警告 (層級 1) C4806
ms.date: 11/04/2016
f1_keywords:
- C4806
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
ms.openlocfilehash: b6fc5708d4e2f9982ceaab57260f13e134e4d247
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578252"
---
# <a name="compiler-warning-level-1-c4806"></a>編譯器警告 (層級 1) C4806

'operation': 不安全的作業：類型 'type' 升至類型 'type' 後沒有值可以等於所給的常數

這個訊息會對程式碼 (例如 `b == 3`) 發出警告，而在程式碼中， `b` 具有類型 `bool`。 提升規則可讓 `bool` 提升成 `int`。 這是合法的，但絕不可為 **true**。 下列範例會產生 C4806：

```
// C4806.cpp
// compile with: /W1
int main()
{
   bool b = true;
   // try..
   // int b = true;

   if (b == 3)   // C4806
   {
      b = false;
   }
}
```