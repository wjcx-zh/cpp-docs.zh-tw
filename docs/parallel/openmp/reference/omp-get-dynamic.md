---
title: "omp_get_dynamic | Microsoft Docs"
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
  - "omp_get_dynamic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_get_dynamic OpenMP function"
ms.assetid: efa843c5-7266-4a75-8db3-22992663d9db
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# omp_get_dynamic
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

傳回值，指出是否執行階段可以調整後續的平行區域中可用的執行緒數量。  
  
## 語法  
  
```  
int omp_get_dynamic();  
```  
  
## 傳回值  
 如果不為零，則會啟用動態調整的執行緒。  
  
## 備註  
 使用指定的執行緒的動態調整[omp\_set\_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)和[OMP\_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)。  
  
 如需詳細資訊，請參閱 [3.1.7 omp\_set\_dynamic Function](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)。  
  
## 範例  
 請參閱[omp\_set\_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)的使用範例， `omp_get_dynamic`。  
  
## 請參閱  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)