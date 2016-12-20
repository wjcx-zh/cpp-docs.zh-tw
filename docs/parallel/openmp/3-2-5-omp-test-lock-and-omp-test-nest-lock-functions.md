---
title: "3.2.5 omp_test_lock and omp_test_nest_lock Functions | Microsoft Docs"
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
ms.assetid: 36818945-c22c-4c24-b754-4e73eba6f3f8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.2.5 omp_test_lock and omp_test_nest_lock Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這些函式會嘗試設定鎖定，但並不會封鎖執行緒的執行。  格式如下：  
  
```  
#include <omp.h>  
int omp_test_lock(omp_lock_t *lock);  
int omp_test_nest_lock(omp_nest_lock_t *lock);  
```  
  
 引數必須指向未初始化的鎖定的變數。  這些函式會嘗試在相同的方式來設定鎖定`omp_set_lock`和`omp_set_nest_lock`，不同之處在於它們並不會封鎖執行緒的執行。  
  
 簡單的鎖定， `omp_test_lock`函式會傳回非零值，如果鎖定就會成功地設定。 否則，它會傳回零。  
  
 Nestable 的鎖定， `omp_test_nest_lock`函式傳回新的巢狀計算，如果鎖定就會成功地設定。 否則，它會傳回零。