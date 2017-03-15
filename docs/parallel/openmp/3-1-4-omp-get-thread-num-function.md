---
title: "3.1.4 omp_get_thread_num Function | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.4 omp_get_thread_num Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`omp_get_thread_num`函式會傳回執行緒，火力，raven，內的數執行函式的執行緒。  執行緒數字就是介於 0 和 **omp\_get\_num\_threads\(\)**– 1，\(含\)。  主要是小組的執行緒 0。  
  
 格式如下：  
  
```  
#include <omp.h>  
int omp_get_thread_num(void);  
```  
  
 如果是從一個序列的地區，呼叫`omp_get_thread_num`會傳回 0。  如果是從呼叫已序列化的巢狀的平行區域內，這個函式會傳回 0。  
  
## 交互參照：  
  
-   `omp_get_num_threads`函式，請參閱[一節 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) 在 37\] 頁面上。