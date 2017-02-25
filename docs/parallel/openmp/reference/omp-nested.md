---
title: "OMP_NESTED | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OMP_NESTED"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OMP_NESTED OpenMP environment variable"
ms.assetid: c43f5287-a548-40d0-bd54-0c6b2b9f9a53
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# OMP_NESTED
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定是否巢狀的平行處理原則已啟用，除非巢狀的平行處理原則已啟用或停用與`omp_set_nested`。  
  
## 語法  
  
```  
set OMP_NESTED[=TRUE | =FALSE]  
```  
  
## 備註  
 `OMP_NESTED`可藉由覆寫環境變數[omp\_set\_nested](../../../parallel/openmp/reference/omp-set-nested.md)函式。  
  
 在 Visual C\+\+ 實作 OpenMP 標準的預設值是`OMP_DYNAMIC=FALSE`。  
  
 如需詳細資訊，請參閱 [4.4 OMP\_NESTED](../../../parallel/openmp/4-4-omp-nested.md)。  
  
## 範例  
 下列指令集`OMP_NESTED`設為 TRUE 的環境變數：  
  
```  
set OMP_NESTED=TRUE  
```  
  
 下列命令會顯示目前設定的`OMP_NESTED`環境變數：  
  
```  
set OMP_NESTED  
```  
  
## 請參閱  
 [Environment Variables](../../../parallel/openmp/reference/openmp-environment-variables.md)