---
title: "使用 lastprivate 子句 A.6 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1744787e1dfb90fa9af93db5dba4eecd600b4334
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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