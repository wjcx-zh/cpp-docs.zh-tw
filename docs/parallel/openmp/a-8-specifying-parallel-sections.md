---
title: A.8 指定平行處理區段 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cf399304-121e-4c07-9829-47e0dbc2ef10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d969f1a0e9d9b282104ee00a3b2d06610533ad4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440416"
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