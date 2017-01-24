---
title: "copyin | Microsoft Docs"
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
  - "copyin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "copyin OpenMP clause"
ms.assetid: 369efa88-613c-4cb1-9e11-7b9ee08a4b25
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# copyin
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

允許執行緒來存取主執行緒的值，如[threadprivate](../../../parallel/openmp/reference/threadprivate.md)變數。  
  
## 語法  
  
```  
copyin(var)  
```  
  
## 備註  
 其中，  
  
 `var`  
 `threadprivate`將會初始化在主執行緒中，變數的值存在於平行建構之前的變數。  
  
## 備註  
 `copyin`適用於下列指示詞：  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 如需詳細資訊，請參閱 [2.7.2.7 copyin](../../../parallel/openmp/2-7-2-7-copyin.md)。  
  
## 範例  
 請參閱[threadprivate](../../../parallel/openmp/reference/threadprivate.md)的使用範例， `copyin`。  
  
## 請參閱  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)