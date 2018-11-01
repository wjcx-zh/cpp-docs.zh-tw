---
title: 編譯器錯誤 C3638
ms.date: 11/04/2016
f1_keywords:
- C3638
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
ms.openlocfilehash: 8b1ef7f4cb38653f0ccdfae5684eb2907a735af7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486884"
---
# <a name="compiler-error-c3638"></a>編譯器錯誤 C3638

'operator': 無法重新定義標準的 boxing 和 unboxing 轉換運算子

編譯器定義轉換運算子，針對每個受管理的類別來支援隱含 boxing。 這個運算子不能重新定義。

如需詳細資訊，請參閱 <<c0> [ 隱含 Boxing](../../windows/boxing-cpp-component-extensions.md)。

下列範例會產生 C3638:

```
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