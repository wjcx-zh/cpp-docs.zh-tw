---
title: 編譯器錯誤 C3052
ms.date: 11/04/2016
f1_keywords:
- C3052
helpviewer_keywords:
- C3052
ms.assetid: 87480c42-1ceb-4775-8d20-88c54a7bb6a6
ms.openlocfilehash: 40857432e07baffea69d8201cc3e0241698c93da
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506209"
---
# <a name="compiler-error-c3052"></a>編譯器錯誤 C3052

'var' : 變數未出現在 default(none) 子句下的資料共用子句中

如果使用了 [default(none)](../../parallel/openmp/reference/openmp-clauses.md#default-openmp) ，任何用在結構化區塊中的變數都必須明確地指定為 [shared](../../parallel/openmp/reference/openmp-clauses.md#shared-openmp) 或 [private](../../parallel/openmp/reference/openmp-clauses.md#private-openmp)。

下列範例會產生 C3052：

```cpp
// C3052.cpp
// compile with: /openmp /c
int main() {
   int n1 = 1;

   #pragma omp parallel default(none) // shared(n1) private(n1)
   {
      n1 = 0;   // C3052 use either a shared or private clause
   }
}
```
