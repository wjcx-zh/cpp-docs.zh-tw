---
title: 編譯器錯誤 C3638
ms.date: 11/04/2016
f1_keywords:
- C3638
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
ms.openlocfilehash: 33bb248faf946c39543de4a14a44e2ebbda49880
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58775227"
---
# <a name="compiler-error-c3638"></a>編譯器錯誤 C3638

'operator': 無法重新定義標準的 boxing 和 unboxing 轉換運算子

編譯器定義轉換運算子，針對每個受管理的類別來支援隱含 boxing。 這個運算子不能重新定義。

如需詳細資訊，請參閱 <<c0> [ 隱含 Boxing](../../extensions/boxing-cpp-component-extensions.md)。

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