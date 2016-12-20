---
title: "3.2.3 omp_set_lock and omp_set_nest_lock Functions | Microsoft Docs"
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
ms.assetid: b5323879-f72e-418e-953f-3979fdda17a2
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.2.3 omp_set_lock and omp_set_nest_lock Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

每個函式會封鎖執行函式，直到指定的鎖定可用，並設定鎖定的執行緒。  簡單的鎖定，則它必須是未鎖定。  Nestable 鎖定是可用，如果它已解除鎖定，或如果它已經被擁有執行函式的執行緒。  格式如下：  
  
```  
#include <omp.h>  
void omp_set_lock(omp_lock_t *lock);  
void omp_set_nest_lock(omp_nest_lock_t *lock);  
```  
  
 簡單的鎖定，以引數的`omp_set_lock`函式必須指向未初始化的鎖定的變數。  執行函式的執行緒是授與鎖定的擁有權。  
  
 Nestable 鎖定的引數的`omp_set_nest_lock`函式必須指向未初始化的鎖定的變數。  巢狀的計數會遞增，而執行緒被授與或會保留鎖定的擁有權。