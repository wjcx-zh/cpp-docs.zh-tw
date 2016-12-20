---
title: "3.2.4 omp_unset_lock and omp_unset_nest_lock Functions | Microsoft Docs"
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
ms.assetid: 5357e43e-a7c0-41d7-b529-3f7d15da8b11
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.2.4 omp_unset_lock and omp_unset_nest_lock Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這些函式可以釋放鎖定的擁有權。  格式如下：  
  
```  
#include <omp.h>  
void omp_unset_lock(omp_lock_t *lock);  
void omp_unset_nest_lock(omp_nest_lock_t *lock);  
```  
  
 每個函式的引數必須指向未執行的函式的執行緒所擁有的初始化的鎖定變數。  這個行為未定義的如果執行緒未擁有該鎖定。  
  
 簡單的鎖定， `omp_unset_lock`函式會釋放鎖定的擁有權從執行函式的執行緒。  
  
 Nestable 的鎖定， `omp_unset_nest_lock`函式會遞減巢狀、 項目個數，並釋放執行緒執行函式從鎖定的擁有權，如果得出的計數為零。