---
title: "firstprivate | Microsoft Docs"
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
  - "firstprivate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "firstprivate OpenMP clause"
ms.assetid: db479766-6d3b-4bbd-b28e-b192d826788c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# firstprivate
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

因為它存在於平行建構之前，請指定每個執行緒都應該有自己的執行個體的變數，並與變數的值，應該先初始化變數。  
  
## 語法  
  
```  
firstprivate(var)  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|`var`|若要讓每個執行緒，並且在執行個體變數將以變數的值，因為它存在於平行建構之前進行初始化。  如果指定一個以上的變數，請以逗號分隔變數名稱。|  
  
## 備註  
  
## 備註  
 `firstprivate`適用於下列指示詞：  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
-   [single](../../../parallel/openmp/reference/single.md)  
  
 如需詳細資訊，請參閱 [2.7.2.2 firstprivate](../../../parallel/openmp/2-7-2-2-firstprivate.md)。  
  
## 範例  
 如需範例，使用的`firstprivate`，請參閱範例[private](../../../parallel/openmp/reference/private-openmp.md)。  
  
## 請參閱  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)