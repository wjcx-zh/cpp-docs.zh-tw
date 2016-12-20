---
title: "3.2 Lock Functions | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 0ec855c6-55a9-49d7-bee4-5edae6e86a1b
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.2 Lock Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這一節所述的函式來操作用於同步處理的鎖定。  
  
 針對下列函式中，鎖定變數必須具有型別 **omp\_lock\_t**。  透過這些函式時，必須只能存取這個變數。  鎖定的所有函數都需要引數具有變數的指標，  **omp\_lock\_t** 型別。  
  
-   `omp_init_lock`函式會初始化簡單的鎖定。  
  
-   `omp_destroy_lock`函數會移除簡單的鎖定。  
  
-   `omp_set_lock`函式會等到簡單的鎖定為止。  
  
-   `omp_unset_lock`函式釋出簡單的鎖定。  
  
-   `omp_test_lock`函式會測試簡單的鎖定。  
  
 針對下列函式中，鎖定變數必須具有型別 **omp\_nest\_lock\_t**。  透過這些函式時，必須只能存取這個變數。  Nestable 鎖定的所有函數都需要引數具有變數的指標，  **omp\_nest\_lock\_t** 型別。  
  
-   `omp_init_nest_lock`函式會初始化 nestable 的鎖定。  
  
-   `omp_destroy_nest_lock`函數會移除 nestable 的鎖定。  
  
-   `omp_set_nest_lock` Nestable 的鎖定，則會提供等候函式。  
  
-   `omp_unset_nest_lock`函式會釋放 nestable 的鎖定。  
  
-   `omp_test_nest_lock`函式會測試 nestable 的鎖定。  
  
 OpenMP 鎖定函式會存取鎖定變數方式，使得它們永遠讀取並更新該鎖定變數的最新的值。  因此，不需要包含外顯 OpenMP 程式**排清**指示詞，以確保鎖定變數的值是不同的執行緒之間的一致性。  \(可能需要**排清**指示詞，可讓其他變數的值一致。\)