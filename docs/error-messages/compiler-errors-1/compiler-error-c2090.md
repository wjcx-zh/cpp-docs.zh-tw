---
title: 編譯器錯誤 C2090
ms.date: 11/04/2016
f1_keywords:
- C2090
helpviewer_keywords:
- C2090
ms.assetid: e8176e55-382b-453d-aa27-6597f0274afd
ms.openlocfilehash: 3c87bc75e984c544646a28a663302acd5733ac25
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755937"
---
# <a name="compiler-error-c2090"></a>編譯器錯誤 C2090

函式傳回陣列

函數無法傳回陣列。 改為傳回陣列的指標。

下列範例會產生 C2090：

```cpp
// C2090.cpp
int func1(void)[] {}   // C2090
```

可能的解決方案：

```cpp
// C2090b.cpp
// compile with: /c
int* func2(int * i) {
   return i;
}
```
