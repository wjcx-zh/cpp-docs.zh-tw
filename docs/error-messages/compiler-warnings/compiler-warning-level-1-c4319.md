---
title: 編譯器警告 （層級 1） C4319 |Microsoft 文件
ms.custom: ''
ms.date: 1/18/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4319
dev_langs:
- C++
helpviewer_keywords:
- C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c1b5fe896ae7d8f43708b60ee4dda486ef08f428
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284741"
---
# <a name="compiler-warning-level-1-c4319"></a>編譯器警告 (層級 1) C4319

> '~': 零擴充'*type1*'to'*type2*' 更大的

結果**~** （位元補充） 運算子時，不帶正負號，然後零擴充轉換到較大的類型。

## <a name="example"></a>範例

在下列範例中，`~(a - 1)`評估為 32 位元不帶正負號的長運算式，然後由零擴充轉換為 64 位元。 這可能會導致非預期的作業結果。

```cpp
// C4319.cpp
// compile with: cl /W4 C4319.cpp
int main() {
   unsigned long a = 0;
   unsigned long long q = 42;
   q = q & ~(a - 1);    // C4319 expected
}
```
