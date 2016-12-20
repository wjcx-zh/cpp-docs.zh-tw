---
title: "omp_get_nested | Microsoft Docs"
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
  - "omp_get_nested"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_get_nested OpenMP function"
ms.assetid: e9784847-516e-40d3-89f7-b8b6898d8667
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# omp_get_nested
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

傳回值，指出是否已啟用巢狀的平行處理原則。  
  
## 語法  
  
```  
int omp_get_nested( );  
```  
  
## 傳回值  
 如果不為零，則會啟用巢狀的平行處理原則。  
  
## 備註  
 巢狀的平行處理原則使用所指定[omp\_set\_nested](../../../parallel/openmp/reference/omp-set-nested.md)和[OMP\_NESTED](../../../parallel/openmp/reference/omp-nested.md)。  
  
 如需詳細資訊，請參閱 [3.1.10 omp\_get\_nested Function](../../../parallel/openmp/3-1-10-omp-get-nested-function.md)。  
  
## 範例  
 請參閱[omp\_set\_nested](../../../parallel/openmp/reference/omp-set-nested.md)的使用範例， `omp_get_nested`。  
  
## 請參閱  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)