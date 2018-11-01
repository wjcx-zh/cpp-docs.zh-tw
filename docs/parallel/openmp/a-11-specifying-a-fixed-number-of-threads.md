---
title: A.11 指定固定的執行緒數目
ms.date: 11/04/2016
ms.assetid: 1d06b142-4c35-44b8-994b-20f2aed5462b
ms.openlocfilehash: 832afac9abc7edd03d3af6f567657aefd596aae0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492036"
---
# <a name="a11---specifying-a-fixed-number-of-threads"></a>A.11 指定固定的執行緒數目

有些程式會依賴固定、 預先指定的數字，要正確執行的執行緒。  因為動態調整的執行緒數目的預設值是由實作定義，這類程式可以選擇關閉動態執行緒功能，並設定明確，以確保可攜性的執行緒數目。 下列範例示範如何使用執行此動作`omp_set_dynamic`([3.1.7 區段](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)39 頁面上)，和`omp_set_num_threads`([區段 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) 36 頁面上):

```
omp_set_dynamic(0);
omp_set_num_threads(16);
#pragma omp parallel shared(x, npoints) private(iam, ipoints)
{
    if (omp_get_num_threads() != 16)
      abort();
    iam = omp_get_thread_num();
    ipoints = npoints/16;
    do_by_16(x, iam, ipoints);
}
```

在此範例中，正確的程式執行只有當它由 16 的執行緒執行。 如果實作不支援執行緒 16，此範例中的行為是由實作定義。

請注意，執行在平行區域的執行緒數目會維持不變期間在平行區域，不論動態設定的執行緒。 動態執行緒機制會決定要在平行區域開始使用的執行緒數目，並讓它常數期間的區域。