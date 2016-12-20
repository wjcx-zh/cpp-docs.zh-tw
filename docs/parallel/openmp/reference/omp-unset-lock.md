---
title: "omp_unset_lock | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_unset_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_unset_lock OpenMP function"
ms.assetid: 68fcb728-040b-4bad-979e-aaecb9097a4e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# omp_unset_lock
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

釋放鎖定。  
  
## 語法  
  
```  
void omp_unset_lock(  
   omp_lock_t *lock  
);  
```  
  
## 備註  
 其中，  
  
 `lock`  
 型別的變數[omp\_lock\_t](../../../parallel/openmp/reference/omp-lock-t.md) ，初始化時[omp\_init\_lock](../../../parallel/openmp/reference/omp-init-lock.md)、 由執行緒擁有和函式中執行。  
  
## 備註  
 如需詳細資訊，請參閱 [3.2.4 omp\_unset\_lock and omp\_unset\_nest\_lock Functions](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md)。  
  
## 範例  
 請參閱[omp\_init\_lock](../../../parallel/openmp/reference/omp-init-lock.md)的使用範例， `omp_unset_lock`。  
  
## 請參閱  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)