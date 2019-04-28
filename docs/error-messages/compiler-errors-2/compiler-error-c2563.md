---
title: 編譯器錯誤 C2563
ms.date: 11/04/2016
f1_keywords:
- C2563
helpviewer_keywords:
- C2563
ms.assetid: 54abba68-6458-4ca5-894d-3babdb7b3552
ms.openlocfilehash: 04a10c82fa6aa39bcf1098d6d4aabfc2f769e7c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257851"
---
# <a name="compiler-error-c2563"></a>編譯器錯誤 C2563

在型式參數清單中的不相符

函式 （或函式的指標） 的型式參數清單不符合的另一個函式 （或成員函式指標）。 如此一來，您無法獲指派的函式或指標。

下列範例會產生 C2563:

```
// C2563.cpp
void func( int );
void func( int, int );
int main() {
   void *fp();
   fp = func;   // C2563
}
```