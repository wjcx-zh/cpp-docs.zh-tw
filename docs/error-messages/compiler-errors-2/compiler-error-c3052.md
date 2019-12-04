---
title: 編譯器錯誤 C3052
ms.date: 11/04/2016
f1_keywords:
- C3052
helpviewer_keywords:
- C3052
ms.assetid: 87480c42-1ceb-4775-8d20-88c54a7bb6a6
ms.openlocfilehash: 618fac69078987b0322739733c403e5b2cd36486
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761214"
---
# <a name="compiler-error-c3052"></a>編譯器錯誤 C3052

'var' : 變數未出現在 default(none) 子句下的資料共用子句中

如果使用了 [default(none)](../../parallel/openmp/reference/default-openmp.md) ，任何用在結構化區塊中的變數都必須明確地指定為 [shared](../../parallel/openmp/reference/shared-openmp.md) 或 [private](../../parallel/openmp/reference/private-openmp.md)。

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
