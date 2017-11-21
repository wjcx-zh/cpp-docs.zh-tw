---
title: "使用平行區域 A.3 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 575216a1-960a-47f7-9c82-7f660291fcfe
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ba7ef5332611a9a6a66a0a0ec5a51461436ef453
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="a3---using-parallel-regions"></a>A.3 使用平行區域
`parallel`指示詞 ([2.3 節](../../parallel/openmp/2-3-parallel-construct.md)在 8 頁面上) 可用於粗略平行的程式。 在下列範例中，每個執行緒在平行區域決定全域陣列的哪個部分`x`運作，根據執行緒數：  
  
```  
#pragma omp parallel shared(x, npoints) private(iam, np, ipoints)  
{  
    iam = omp_get_thread_num();  
    np =  omp_get_num_threads();  
    ipoints = npoints / np;  
    subdomain(x, iam, ipoints);  
}  
```