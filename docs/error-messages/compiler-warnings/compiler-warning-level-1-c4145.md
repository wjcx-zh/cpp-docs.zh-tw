---
title: 編譯器警告 (層級 1) C4145
ms.date: 11/04/2016
f1_keywords:
- C4145
helpviewer_keywords:
- C4145
ms.assetid: 0440777a-cca2-4159-aff5-e67a254ad64a
ms.openlocfilehash: 19d2d1a018c7ee981f83aa6fa0914f1241c55538
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220102"
---
# <a name="compiler-warning-level-1-c4145"></a>編譯器警告 (層級 1) C4145

'expression1': 關聯運算式作為 switch 運算式；可能與 '%$L' 混淆

**`switch`** 語句會使用關聯式運算式做為其控制運算式，這會導致語句的布林值 **`case`** 。 您是不是指 *expression2*？

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
