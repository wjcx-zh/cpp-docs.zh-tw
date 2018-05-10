---
title: 使用 lastprivate 子句 A.6 |Microsoft 文件
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
ms.openlocfilehash: eec6ddc46aab36671e767963e5aaf6e25c4d25cd
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="a6---using-the-lastprivate-clause"></a>A.6 使用 lastprivate 子句
有時正確執行取決於迴圈的最後一個反覆項目指派給變數的值。 這類程式必須列出所有這類變數做為引數`lastprivate`子句 ([區段 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) 27 頁面上)，讓變數的值與迴圈執行時以循序方式相同。  
  
```  
#pragma omp parallel  
{  
   #pragma omp for lastprivate(i)  
      for (i=0; i<n-1; i++)  
         a[i] = b[i] + b[i+1];  
}  
a[i]=b[i];  
```  
  
 在上述範例中，值`i`在平行區域結尾處將等於`n-1`，在循序的案例中。