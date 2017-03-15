---
title: "omp_destroy_nest_lock | Microsoft Docs"
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
  - "omp_destroy_nest_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_destroy_nest_lock OpenMP function"
ms.assetid: 0ab1352b-668f-43dd-b441-31ec4cc53e68
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# omp_destroy_nest_lock
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

未初始化的 nestable 鎖定。  
  
## 語法  
  
```  
void omp_destroy_nest_lock(  
   omp_nest_lock_t *lock  
);  
```  
  
## 備註  
 其中，  
  
 `lock`  
 型別的變數[omp\_nest\_lock\_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) ，初始化時[omp\_init\_nest\_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)。  
  
## 備註  
 如需詳細資訊，請參閱 [3.2.2 omp\_destroy\_lock and omp\_destroy\_nest\_lock Functions](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md)。  
  
## 範例  
 請參閱[omp\_init\_nest\_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)的使用範例， `omp_destroy_nest_lock`。  
  
## 請參閱  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)