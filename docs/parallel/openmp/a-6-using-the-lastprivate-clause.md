---
title: A.6 使用 lastprivate 子句 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03d18d3aaf5c5d1cbe03282710ae4f4e2bb613f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390574"
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