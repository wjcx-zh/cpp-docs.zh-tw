---
title: "3.1.4 omp_get_thread_num 函式 |Microsoft 文件"
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
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b7b968d103631dafcdd2132cb749ae8feed30085
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="314-ompgetthreadnum-function"></a>3.1.4 omp_get_thread_num 函式
`omp_get_thread_num`函式會傳回執行緒數目，其小組中，執行此函式的執行緒。 執行緒數字就是介於 0 和**omp_get_num_threads()**-1，（含)。 主要的小組是執行緒 0。  
  
 格式如下：  
  
```  
#include <omp.h>  
int omp_get_thread_num(void);  
```  
  
 如果序列的區域中，從呼叫`omp_get_thread_num`傳回 0。 如果從序列化巢狀平行區域內呼叫，此函式會傳回 0。  
  
## <a name="cross-references"></a>交叉參考：  
  
-   `omp_get_num_threads`函式，請參閱[區段 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) 37 頁面上。