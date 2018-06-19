---
title: 指定平行區段 A.8 |Microsoft 文件
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
ms.openlocfilehash: acb28f4e7e99ea09696d116ab031778fcf9ff919
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694052"
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