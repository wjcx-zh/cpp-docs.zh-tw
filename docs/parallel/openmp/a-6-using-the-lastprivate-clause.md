---
title: A.6 使用 lastprivate 子句
ms.date: 11/04/2016
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
ms.openlocfilehash: 7d5ba1413827590b7fb3afa0847b9aa1da3c41e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579799"
---
# <a name="a6---using-the-lastprivate-clause"></a>A.6 使用 lastprivate 子句

有時候使用正確的執行取決於迴圈的最後一個反覆項目指派給變數的值。 這種程式都必須列出所有這類變數做為引數`lastprivate`子句 ([區段 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) 27 頁面上)，讓變數的值會與迴圈執行時以循序方式相同。

```
#pragma omp parallel
{
   #pragma omp for lastprivate(i)
      for (i=0; i<n-1; i++)
         a[i] = b[i] + b[i+1];
}
a[i]=b[i];
```

在上述範例中，值`i`結尾的平行區域將會等於`n-1`，如所示的循序的情況。