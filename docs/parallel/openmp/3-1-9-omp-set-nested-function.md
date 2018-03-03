---
title: "3.1.9 omp_set_nested 函式 |Microsoft 文件"
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
ms.assetid: e4afc3aa-bb96-4314-9849-fd5df5f437d9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0910e7df0ebd423b9967fd0eb7931b7434ba94fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="319-ompsetnested-function"></a>3.1.9 omp_set_nested 函式
**Omp_set_nested**函式啟用或停用巢狀平行處理原則。 格式如下：  
  
```  
#include <omp.h>  
void omp_set_nested(int nested);  
```  
  
 如果*巢狀*判斷值為 0，巢狀平行處理原則已停用，這是預設值，並序列化和目前的執行緒執行的巢狀平行區域。 如果*巢狀*評估為非零值，已啟用巢狀平行處理原則，以及巢狀平行區域可以部署額外的執行緒，以形成巢狀的小組。  
  
 此函式可從程式的一部分呼叫時，上面所述的效果其中**omp_in_parallel**函式會傳回零。 如果從程式的一部分呼叫其中**omp_in_parallel**函式會傳回非零值，這個函式的行為是未定義。  
  
 這個呼叫的優先順序高於**OMP_NESTED**環境變數。  
  
 啟用巢狀平行處理原則時，用來執行巢狀平行區域的執行緒數目是由實作定義。 如此一來，OpenMP 符合實作允許序列化巢狀平行區域，即使已啟用巢狀平行處理原則。  
  
## <a name="cross-references"></a>交叉參考：  
  
-   **OMP_NESTED**環境變數，請參閱[區段 4.4](../../parallel/openmp/4-4-omp-nested.md) 49 頁面上。  
  
-   **omp_in_parallel**函式，請參閱[區段 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md)在 38 頁面上。