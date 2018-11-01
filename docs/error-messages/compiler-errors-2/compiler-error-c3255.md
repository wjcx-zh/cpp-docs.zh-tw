---
title: 編譯器錯誤 C3255
ms.date: 11/04/2016
f1_keywords:
- C3255
helpviewer_keywords:
- C3255
ms.assetid: 877ffca2-fd92-44b6-9060-6091b928b1c1
ms.openlocfilehash: a5b483f3aaa82e543d561cb7c550495069a19f7c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519934"
---
# <a name="compiler-error-c3255"></a>編譯器錯誤 C3255

'實值型別': 無法以動態方式配置這個原生堆積上的實值類型物件

實值類型的執行個體 (請參閱[類別和結構](../../windows/classes-and-structs-cpp-component-extensions.md))，其中包含受管理的成員可以在堆疊上，但不是在堆積上建立。

下列範例會產生 C3255:

```
// C3255.cpp
// compile with: /clr
using namespace System;
value struct V {
   Object^ o;
};

value struct V2 {
   int i;
};

int main() {
   V* pv = new V;   // C3255
   V2* pv2 = new V2;
   V v2;
}
```
