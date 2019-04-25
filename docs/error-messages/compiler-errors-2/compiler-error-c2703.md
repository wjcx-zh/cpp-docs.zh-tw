---
title: 編譯器錯誤 C2703
ms.date: 11/04/2016
f1_keywords:
- C2703
helpviewer_keywords:
- C2703
ms.assetid: 384295c3-643d-47ae-a9a6-865b3036aa84
ms.openlocfilehash: 363e3de497a7226a7c1dddd5769a047e6ea53e29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161390"
---
# <a name="compiler-error-c2703"></a>編譯器錯誤 C2703

不合法的 __leave 陳述式

A`__leave`陳述式必須是內部`__try`區塊。

下列範例會產生 C2703:

```
// C2703.cpp
int main() {
   __leave;   // C2703
   __try {
      // try the following line instead
      __leave;
   }
   __finally {}
}
```