---
title: "編譯器警告 （層級 1） C4319 |Microsoft 文件"
ms.custom: 
ms.date: 1/18/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4319
dev_langs:
- C++
helpviewer_keywords:
- C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a492194003a639f684e84d125450067cd425276
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="compiler-warning-level-1-c4319"></a>編譯器警告 (層級 1) C4319

> '~': 零擴充'*type1*'to'*type2*' 更大的

結果 **~**  （位元補充） 運算子時，不帶正負號，然後零擴充轉換到較大的類型。

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
