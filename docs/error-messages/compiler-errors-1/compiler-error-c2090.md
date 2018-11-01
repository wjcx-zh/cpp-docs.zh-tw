---
title: 編譯器錯誤 C2090
ms.date: 11/04/2016
f1_keywords:
- C2090
helpviewer_keywords:
- C2090
ms.assetid: e8176e55-382b-453d-aa27-6597f0274afd
ms.openlocfilehash: d805a4d6e0da0e94288ac36c6680a952b7633b86
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469390"
---
# <a name="compiler-error-c2090"></a>編譯器錯誤 C2090

函式會傳回陣列

函式無法傳回陣列。 改為傳回陣列的指標。

下列範例會產生 C2090:

```
// C2090.cpp
int func1(void)[] {}   // C2090
```

可能的解決方式：

```
// C2090b.cpp
// compile with: /c
int* func2(int * i) {
   return i;
}
```