---
title: 編譯器錯誤 C2675
ms.date: 11/04/2016
f1_keywords:
- C2675
helpviewer_keywords:
- C2675
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
ms.openlocfilehash: aea79509d0e1ae5c31fcf0cf369c28af39a21154
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499823"
---
# <a name="compiler-error-c2675"></a>編譯器錯誤 C2675

一元 'operator': 'type' 不會定義此運算子或可接受的類型轉換至預先定義的運算子

C2675 也可能發生於使用一元運算子，而且類型未定義運算子或可接受的類型轉換至預先定義的運算子。 若要使用運算子，您必須針對指定類型進行多載，或針對已定義運算子的類型定義轉換。

## <a name="example"></a>範例

下列範例會產生 C2675。

```
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