---
title: 編譯器錯誤 C2563
ms.date: 11/04/2016
f1_keywords:
- C2563
helpviewer_keywords:
- C2563
ms.assetid: 54abba68-6458-4ca5-894d-3babdb7b3552
ms.openlocfilehash: 983788f041651fcd313c0707a4a7c64cc6e33c5a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755534"
---
# <a name="compiler-error-c2563"></a>編譯器錯誤 C2563

型式參數清單中的不相符

函式的型式參數清單（或函式的指標）與另一個函式（或成員函式的指標）不相符。 因此，無法建立函數或指標的指派。

下列範例會產生 C2563：

```cpp
// C2563.cpp
void func( int );
void func( int, int );
int main() {
   void *fp();
   fp = func;   // C2563
}
```
