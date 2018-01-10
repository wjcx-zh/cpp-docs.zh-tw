---
title: "使用的重要指示詞 A.5 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 14423018-25b9-4f98-92f2-34c9b0ac0ce0
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7cf4170fae6792906db29c90f61f067886b00f1d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="a5---using-the-critical-directive"></a>A.5 使用 critical 指示詞
下列範例包含數個`critical`指示詞 ([區段 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md)第 18 頁上)。 此範例說明工作會清除佇列並處理過的佇列模型。 若要防範取消佇列相同的工作的多個執行緒，清除佇列作業必須在`critical`> 一節。 在此範例中的兩個佇列無關，因為它們由保護`critical`具有不同的名稱，指示詞*xaxis*和*y 軸*。  
  
```  
#pragma omp parallel shared(x, y) private(x_next, y_next)  
{  
    #pragma omp critical ( xaxis )  
        x_next = dequeue(x);  
    work(x_next);  
    #pragma omp critical ( yaxis )  
        y_next = dequeue(y);  
    work(y_next);  
}  
```