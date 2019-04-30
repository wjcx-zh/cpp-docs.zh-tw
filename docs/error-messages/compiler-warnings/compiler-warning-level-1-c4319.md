---
title: 編譯器警告 (層級 1) C4319
ms.date: 1/18/2018
f1_keywords:
- C4319
helpviewer_keywords:
- C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
ms.openlocfilehash: 20b268bacd6e7e259e9b4fa1c9e98fa6fd353718
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385468"
---
# <a name="compiler-warning-level-1-c4319"></a>編譯器警告 (層級 1) C4319

> '~': 零擴充'*type1*'到'*type2*' 更大的

結果**~** （位元補充） 運算子時，不帶正負號，然後零擴充轉換到較大的類型。

## <a name="example"></a>範例

在下列範例中，`~(a - 1)`是評估為 32 位元不帶正負號長的運算式，然後由零擴充轉換為 64 位元。 這可能會導致非預期的作業結果。

```cpp
// C4319.cpp
// compile with: cl /W4 C4319.cpp
int main() {
   unsigned long a = 0;
   unsigned long long q = 42;
   q = q & ~(a - 1);    // C4319 expected
}
```
