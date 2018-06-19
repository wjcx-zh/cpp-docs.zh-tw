---
title: 決定使用的執行緒數目 A.15 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 026bb59a-f668-40db-a7cb-69a1bae83d2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b50858a3384fa5f8d867f13a699e1fc271c101ef
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686382"
---
# <a name="a15---determining-the-number-of-threads-used"></a>A.15 判斷使用的執行緒數目
請考慮下列不正確的範例 (如[區段 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) 37 頁面上):  
  
```  
np = omp_get_num_threads(); // misplaced   
#pragma omp parallel for schedule(static)  
    for (i=0; i<np; i++)  
        work(i);  
```  
  
 `omp_get_num_threads()`序列一節的程式碼，呼叫傳回 1，因此*np*一定會在上述範例中為 1 相等。 若要判斷將部署的平行區域的執行緒數目，呼叫應該會在平行區域內。  
  
 下列範例顯示如何不包括的執行緒數目的查詢重新撰寫此程式：  
  
```  
#pragma omp parallel private(i)  
{  
    i = omp_get_thread_num();  
    work(i);  
}  
```