---
title: 編譯器錯誤 C2640
ms.date: 11/04/2016
f1_keywords:
- C2640
helpviewer_keywords:
- C2640
ms.assetid: e4d137ab-ed1d-457c-9eec-b70d97f1b0b4
ms.openlocfilehash: eb712379ff3ce25a435f4810f5552bc97f635cdd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212679"
---
# <a name="compiler-error-c2640"></a>編譯器錯誤 C2640

' identifier '：參考時 __based 修飾詞不合法

修飾詞只能 **`__based`** 用於指標。

下列範例會產生 C2640：

```cpp
// C2640.cpp
void f(int i) {
    void *vp;
    int _based(vp) &vr = I;  // C2640
}
```
