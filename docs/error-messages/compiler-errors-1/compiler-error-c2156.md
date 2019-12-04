---
title: 編譯器錯誤 C2156
ms.date: 11/04/2016
f1_keywords:
- C2156
helpviewer_keywords:
- C2156
ms.assetid: 136f9c67-2c27-4f61-b7e6-ccd202eca697
ms.openlocfilehash: da8a5a9bcdeb33a9b308e24b129fded0595449a3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755898"
---
# <a name="compiler-error-c2156"></a>編譯器錯誤 C2156

Pragma 必須定義在函式之外

必須在全域層級 (函式主體外部) 指定的 pragma 出現在函式內。

下列範例會產生 C2156：

```cpp
// C2156.cpp
#pragma optimize( "l", on )   // OK
int main() {
   #pragma optimize( "l", on )   // C2156
}
```
