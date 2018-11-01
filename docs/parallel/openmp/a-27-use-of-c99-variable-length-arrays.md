---
title: A.27 使用 C99 可變長度陣列
ms.date: 11/04/2016
ms.assetid: 8e542701-39f9-4f28-ab3a-840e8e669723
ms.openlocfilehash: 7b2ee74dcd5adedd02e7a9b311c5d3f67203d892
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655295"
---
# <a name="a27---use-of-c99-variable-length-arrays"></a>A.27 使用 C99 可變長度陣列

下列範例會示範如何使用 C99 可變長度陣列 (Vla) 中`firstprivate`指示詞 ([一節 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md)在 26 頁面上)。

> [!NOTE]
>  可變長度陣列目前不支援 Visual c + +。

```
void f(int m, int C[m][m])
{
    double v1[m];
    ...
    #pragma omp parallel firstprivate(C, v1)
    ...
}
```