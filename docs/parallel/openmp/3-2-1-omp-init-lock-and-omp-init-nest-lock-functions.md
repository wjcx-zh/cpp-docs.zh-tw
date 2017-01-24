---
title: "3.2.1 omp_init_lock and omp_init_nest_lock Functions | Microsoft Docs"
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
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.2.1 omp_init_lock and omp_init_nest_lock Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這些函式會提供初始化鎖定的唯一方法。  每個函式會初始化與參數相關聯的鎖定*鎖定*用於後續的呼叫。  格式如下：  
  
```  
#include <omp.h>  
void omp_init_lock(omp_lock_t *lock);  
void omp_init_nest_lock(omp_nest_lock_t *lock);  
```  
  
 初始的狀態都已解除鎖定 \(也就是沒有執行緒擁有的鎖定\)。  Nestable 的鎖定，初始的巢狀計數為零。  它會呼叫這些常式已經初始化為鎖定變數的任何一個不相容。