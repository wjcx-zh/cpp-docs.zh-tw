---
title: 3.1.4 omp_get_thread_num 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fad749b91470f7834169fe8ed734f1d627aa228e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686067"
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
  
-   `omp_get_num_threads` 函式，請參閱[區段 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) 37 頁面上。