---
title: "指定平行區段 A.8 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: cf399304-121e-4c07-9829-47e0dbc2ef10
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db7decc4efb1a3f6bb457623489c84e0ad1ae1f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="a8---specifying-parallel-sections"></a>A.8 指定平行處理區段
在下列範例中，(如[區段 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md)在頁面上 14) 函式*xaxis*， *y 軸*，和*zaxis*可同時執行。 第一個`section`指示詞是選擇性的。  請注意，所有`section`指示詞需要的語彙範圍中出現`parallel sections`建構。  
  
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