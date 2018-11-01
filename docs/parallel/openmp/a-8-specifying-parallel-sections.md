---
title: A.8 指定平行處理區段
ms.date: 11/04/2016
ms.assetid: cf399304-121e-4c07-9829-47e0dbc2ef10
ms.openlocfilehash: 81eaed920e77b23052ac58c2d0e18fee83c00565
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461434"
---
# <a name="a8---specifying-parallel-sections"></a>A.8 指定平行處理區段

在下列範例中，(針對[一節 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md)在 14 頁面上) 函式*xaxis*， *y 軸*，和*zaxis*可以並行執行。 第一個`section`指示詞是選擇性的。  請注意，所有`section`指示詞需要的語彙範圍中出現`parallel sections`建構。

```
#pragma omp parallel sections
{
    #pragma omp section
        xaxis();
    #pragma omp section
        yaxis();
    #pragma omp section
        zaxis();
}
```