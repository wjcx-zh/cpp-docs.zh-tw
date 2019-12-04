---
title: 編譯器錯誤 C2675
ms.date: 11/04/2016
f1_keywords:
- C2675
helpviewer_keywords:
- C2675
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
ms.openlocfilehash: 0b7b81ce7314fbad02d6873403fc5cf1bdd54709
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760370"
---
# <a name="compiler-error-c2675"></a>編譯器錯誤 C2675

一元 ' operator '： ' type ' 未定義此運算子或預先定義運算子可接受的類型轉換

使用一元運算子時也可能會發生 C2675，而且類型不會定義運算子或預先定義運算子可接受之類型的轉換。 若要使用運算子，您必須針對指定類型進行多載，或針對已定義運算子的類型定義轉換。

## <a name="example"></a>範例

下列範例會產生 C2675。

```cpp
// C2675.cpp
struct C {
   C(){}
} c;

struct D {
   D(){}
   void operator-(){}
} d;

int main() {
   -c;   // C2675
   -d;   // OK
}
```
