---
title: "omp_set_nest_lock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_set_nest_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_set_nest_lock OpenMP function"
ms.assetid: b98ed889-ff8e-4217-a3e9-3993ed8699af
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# omp_set_nest_lock
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

封鎖執行緒執行，直到鎖定可用為止。  
  
## 語法  
  
```  
void omp_set_nest_lock(  
   omp_nest_lock_t *lock  
);  
```  
  
## 備註  
 其中，  
  
 `lock`  
 型別的變數[omp\_nest\_lock\_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) ，初始化時[omp\_init\_nest\_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)。  
  
## 備註  
 如需詳細資訊，請參閱 [3.2.3 omp\_set\_lock and omp\_set\_nest\_lock Functions](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md)。  
  
## 範例  
 請參閱[omp\_init\_nest\_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)的使用範例， `omp_set_nest_lock`。  
  
## 請參閱  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)