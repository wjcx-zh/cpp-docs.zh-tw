---
title: A.1 平行執行簡單迴圈 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b8aaacae-b20d-4b16-a540-54ccbf09582b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b5446f72cc5ee0577385527be24bc912297aec0d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418940"
---
# <a name="a1---executing-a-simple-loop-in-parallel"></a>A.1 平行執行簡單迴圈

下列範例示範如何平行處理簡單的迴圈，使用`parallel for`指示詞 ([一節 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md)上 16)。 迴圈反覆項目變數是預設的情況下，私人的因此不需要明確指定 private 子句中。

```
#pragma omp parallel for
    for (i=1; i<n; i++)
        b[i] = (a[i] + a[i-1]) / 2.0;
```