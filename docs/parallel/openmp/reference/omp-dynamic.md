---
title: "OMP_DYNAMIC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OMP_DYNAMIC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OMP_DYNAMIC OpenMP environment variable"
ms.assetid: e306049d-b644-4b73-8b63-46c835bff98b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# OMP_DYNAMIC
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定執行階段 OpenMP 是否可以調整在平行區域中的執行緒數目。  
  
## 語法  
  
```  
set OMP_DYNAMIC[=TRUE | =FALSE]  
```  
  
## 備註  
 `OMP_DYNAMIC`可藉由覆寫環境變數[omp\_set\_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)函式。  
  
 在 Visual C\+\+ 實作 OpenMP 標準的預設值是`OMP_DYNAMIC=FALSE`。  
  
 如需詳細資訊，請參閱 [4.3 OMP\_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md)。  
  
## 範例  
 下列指令集`OMP_DYNAMIC`設為 TRUE 的環境變數：  
  
```  
set OMP_DYNAMIC=TRUE  
```  
  
 下列命令會顯示目前設定的`OMP_DYNAMIC`環境變數：  
  
```  
set OMP_DYNAMIC  
```  
  
## 請參閱  
 [Environment Variables](../../../parallel/openmp/reference/openmp-environment-variables.md)