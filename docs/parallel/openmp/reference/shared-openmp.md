---
title: "shared (OpenMP) | Microsoft Docs"
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
  - "Shared"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "shared OpenMP clause"
ms.assetid: 7887dc95-67a2-462f-a3a2-8e0632bf5d04
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# shared (OpenMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定一或多個變數應該分擔所有執行緒。  
  
## 語法  
  
```  
shared(var)  
```  
  
## 備註  
 其中，  
  
 `var`  
 若要共用的一個更多個變數。  如果指定一個以上的變數，請以逗號分隔變數名稱。  
  
## 備註  
 共用變數在執行緒之間的另一個解決方式是使用[copyprivate](../../../parallel/openmp/reference/copyprivate.md)子句。  
  
 `shared`適用於下列指示詞：  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 如需詳細資訊，請參閱 [2.7.2.4 shared](../../../parallel/openmp/2-7-2-4-shared.md)。  
  
## 範例  
 請參閱[private](../../../parallel/openmp/reference/private-openmp.md)的使用範例， `shared`。  
  
## 請參閱  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)