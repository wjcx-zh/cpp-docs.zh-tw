---
title: 編譯器警告 (層級 1) C4145
ms.date: 11/04/2016
f1_keywords:
- C4145
helpviewer_keywords:
- C4145
ms.assetid: 0440777a-cca2-4159-aff5-e67a254ad64a
ms.openlocfilehash: a6ae6145749842c01e720f5af1fe2b3ee438a5ba
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624995"
---
# <a name="compiler-warning-level-1-c4145"></a>編譯器警告 (層級 1) C4145

'expression1': 關聯運算式作為 switch 運算式；可能與 '%$L' 混淆

`switch` 陳述式使用關聯運算式作為其控制運算式，因而導致 **case** 陳述式的布林值。 您是不是指 *expression2*？

## <a name="example"></a>範例

下列範例會產生 C4145：

```cpp
// C4145.cpp
// compile with: /W1
int main() {
   int i = 0;
   switch(i == 1) {   // C4145, use i instead of i == 1 to resolve
      case 1:
         break;
      default:
         break;
   }
}
```