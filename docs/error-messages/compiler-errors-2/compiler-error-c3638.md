---
title: 編譯器錯誤 C3638
ms.date: 11/04/2016
f1_keywords:
- C3638
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
ms.openlocfilehash: f8d67ac0ff6a1fa5d9efbb8d85747ff94d75c648
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742492"
---
# <a name="compiler-error-c3638"></a>編譯器錯誤 C3638

' operator '：無法重新定義標準的裝箱和取消裝箱轉換運算子

編譯器會針對每個 managed 類別定義轉換運算子，以支援隱含的裝箱。 無法重新定義此運算子。

如需詳細資訊，請參閱[隱含的裝箱](../../extensions/boxing-cpp-component-extensions.md)。

下列範例會產生 C3638：

```cpp
// C3638.cpp
// compile with: /clr
value struct V {
   V(){}
   static operator V^(V);   // C3638
};

int main() {
   V myV;
   V ^ pmyV = myV;   // operator supports implicit boxing
}
```
