---
title: 以平行方式執行簡單的迴圈 A.1 |Microsoft 文件
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
ms.openlocfilehash: 98b2fbac6ce31d2dbc56a4ef6d9fe87c14d5ee16
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686122"
---
# <a name="a1---executing-a-simple-loop-in-parallel"></a>A.1 平行執行簡單迴圈
下列範例示範如何平行處理簡單迴圈使用`parallel for`指示詞 ([區段 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md)在頁面上 16)。 迴圈反覆運算變數是根據預設，私用，因此不需要明確指定 private 子句中。  
  
```  
#pragma omp parallel for  
    for (i=1; i<n; i++)  
        b[i] = (a[i] + a[i-1]) / 2.0;  
```