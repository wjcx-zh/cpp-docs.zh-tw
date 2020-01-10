---
title: 編譯器錯誤 C3255
ms.date: 11/04/2016
f1_keywords:
- C3255
helpviewer_keywords:
- C3255
ms.assetid: 877ffca2-fd92-44b6-9060-6091b928b1c1
ms.openlocfilehash: 43538ce87e1d832fcfc4fca882a9f129b917aad5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754208"
---
# <a name="compiler-error-c3255"></a>編譯器錯誤 C3255

' 實數值型別 '：無法在原生堆積上動態配置此實數值型別物件

包含 managed 成員的實數值型別實例（請參閱[類別和結構](../../extensions/classes-and-structs-cpp-component-extensions.md)）可以在堆疊上建立，而不是在堆積上。

下列範例會產生 C3255：

```cpp
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
