---
title: "omp_destroy_lock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_destroy_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_destroy_lock OpenMP function"
ms.assetid: b73ab036-b76f-4e42-82ff-c89db2edf7c0
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# omp_destroy_lock
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

未初始化鎖定。  
  
## 語法  
  
```  
void omp_destroy_lock(  
   omp_lock_t *lock  
);  
```  
  
## 備註  
 其中，  
  
 `lock`  
 型別的變數[omp\_lock\_t](../../../parallel/openmp/reference/omp-lock-t.md) ，初始化時[omp\_init\_lock](../../../parallel/openmp/reference/omp-init-lock.md)。  
  
## 備註  
 如需詳細資訊，請參閱 [3.2.2 omp\_destroy\_lock and omp\_destroy\_nest\_lock Functions](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md)。  
  
## 範例  
 請參閱[omp\_init\_lock](../../../parallel/openmp/reference/omp-init-lock.md)的使用範例， `omp_destroy_lock`。  
  
## 請參閱  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)