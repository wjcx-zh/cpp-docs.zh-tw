---
title: "指定固定的執行緒數目 A.11 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 1d06b142-4c35-44b8-994b-20f2aed5462b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 72c8aca2b90f021771ba9f9fc8a86d784ffe24a9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="a11---specifying-a-fixed-number-of-threads"></a>A.11 指定固定的執行緒數目
有些程式依賴固定、 預先指定的數字，要正確執行的執行緒。  動態調整的執行緒數目的預設值是由實作定義，因為這類程式可以選擇關閉動態執行緒功能和設定明確地確保可攜性的執行緒數目。 下列範例示範如何使用執行此動作`omp_set_dynamic`([區段 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 39 頁面上)，和`omp_set_num_threads`([區段 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) 36 頁面上):  
  
```  
omp_set_dynamic(0);  
omp_set_num_threads(16);  
#pragma omp parallel shared(x, npoints) private(iam, ipoints)  
{  
    if (omp_get_num_threads() != 16)   
      abort();  
    iam = omp_get_thread_num();  
    ipoints = npoints/16;  
    do_by_16(x, iam, ipoints);  
}  
```  
  
 在此範例中，程式會由 16 執行緒執行，則只有正確執行。 如果實作是不支援執行緒 16，此範例的行為是由實作定義。  
  
 請注意，執行在平行區域的執行緒數目會維持不變，不論設定的動態執行緒在平行區域期間。 動態執行緒機制會決定要在平行區域開始使用的執行緒數目，並會保留它常數之區域的持續時間。