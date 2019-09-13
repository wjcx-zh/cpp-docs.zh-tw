---
title: 編譯器警告 (層級 1) C4319
ms.date: 01/18/2018
f1_keywords:
- C4319
helpviewer_keywords:
- C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
ms.openlocfilehash: 2d5ae8fcf5a527031c3a974b227f713675f31ffa
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926107"
---
# <a name="compiler-warning-level-1-c4319"></a>編譯器警告 (層級 1) C4319

> ' ~ '：零將 '*type1*' 延伸至較大的 '*type2*'

**~** （位補數）運算子的結果不帶正負號，然後在轉換成較大的類型時以零擴充。

## <a name="example"></a>範例

在下列範例中， `~(a - 1)`會評估為32位不帶正負號的長運算式，然後轉換為64位（以零為起始）。 這可能會導致非預期的作業結果。

```cpp
// C4319.cpp
// compile with: cl /W4 C4319.cpp
int main() {
   unsigned long a = 0;
   unsigned long long q = 42;
   q = q & ~(a - 1);    // C4319 expected
}
```
