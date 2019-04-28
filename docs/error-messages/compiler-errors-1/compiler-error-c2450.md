---
title: 編譯器錯誤 C2450
ms.date: 11/04/2016
f1_keywords:
- C2450
helpviewer_keywords:
- C2450
ms.assetid: 929f1c06-8774-468b-be2a-f428757875a2
ms.openlocfilehash: 3cbab274f8f7cd04d5fb86db69572e0b7fc1c04e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208967"
---
# <a name="compiler-error-c2450"></a>編譯器錯誤 C2450

類型 'type' 的 switch 運算式不合法

`switch`運算式評估為無效的類型。 它必須評估為整數類型或類別類型模稜兩可的轉換為整數類型。 如果它評估成使用者定義型別，您必須提供轉換運算子。

下列範例會產生 C2450:

```
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