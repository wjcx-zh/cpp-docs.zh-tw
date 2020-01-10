---
title: 編譯器錯誤 C2450
ms.date: 11/04/2016
f1_keywords:
- C2450
helpviewer_keywords:
- C2450
ms.assetid: 929f1c06-8774-468b-be2a-f428757875a2
ms.openlocfilehash: 2d015bd165986467a82f33a2ae0dda08c6f6d248
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744143"
---
# <a name="compiler-error-c2450"></a>編譯器錯誤 C2450

類型 ' type ' 的切換運算式不合法

`switch` 運算式會評估為不正確類型。 它必須評估為整數類型，或是明確轉換成整數類型的類別類型。 如果評估為使用者定義的型別，您就必須提供轉換運算子。

下列範例會產生 C2450：

```cpp
// C2450.cpp
class X {
public:
   int i;
} x;

class Y {
public:
   int i;
   operator int() { return i; }   // conversion operator
} y;

int main() {
   int j = 1;
   switch ( x ) {   // C2450, x is not type int
   // try the following line instead
   // switch ( y ) {
      default:  ;
   }
}
```
