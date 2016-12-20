---
title: "default (OpenMP) | Microsoft Docs"
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
  - "default"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "default OpenMP clause"
  - "defaults, OpenMP clause"
ms.assetid: 96055106-a8f0-40b3-8319-e412b6e07bf8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# default (OpenMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定在平行區域中的 unscoped 變數的行為。  
  
## 語法  
  
```  
default(shared | none)  
```  
  
## 備註  
 `shared`這實際上是如果`default`未指定子句，則表示在平行區域中的任何變數將會被視為如同在它被指定為使用[shared](../../../parallel/openmp/reference/shared-openmp.md)子句。  `none`指的不是範圍與在平行區域中使用的任何變數[private](../../../parallel/openmp/reference/private-openmp.md)， [shared](../../../parallel/openmp/reference/shared-openmp.md)， [reduction](../../../parallel/openmp/reference/reduction.md)， [firstprivate](../../../parallel/openmp/reference/firstprivate.md)，或[lastprivate](../../../parallel/openmp/reference/lastprivate.md)子句會引起編譯器錯誤。  
  
 `default`適用於下列指示詞：  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 如需詳細資訊，請參閱 [2.7.2.5 default](../../../parallel/openmp/2-7-2-5-default.md)。  
  
## 範例  
 請參閱[private](../../../parallel/openmp/reference/private-openmp.md)的使用範例， `default`。  
  
## 請參閱  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)