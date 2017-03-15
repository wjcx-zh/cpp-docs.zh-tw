---
title: "F. New Features and Clarifications in Version 2.0 | Microsoft Docs"
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
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# F. New Features and Clarifications in Version 2.0
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本附錄摘要關鍵 OpenMP C\/C\+\+ 規格中從 1.0 版移到 2.0 版中所做的變更。  下列項目會新增到規格的新功能：  
  
-   OpenMP 指示詞中允許逗點 \([2.1 節](../../parallel/openmp/2-1-directive-format.md)在頁面上 7\)。  
  
-   額外的`num_threads`子句。  這個子句可讓使用者要求特定數目的執行緒的平行建構 \([2.3 節](../../parallel/openmp/2-3-parallel-construct.md)在頁面上 8\)。  
  
-   `threadprivate`指示詞已經擴充以接受靜態的區塊範圍變數 \([一節 2.7.1](../../parallel/openmp/2-7-1-threadprivate-directive.md) 第 23 頁\)。  
  
-   C99 變數長度的陣列是完整的型別，並因此可以指定任何一處完整的型別，舉個例說中允許的清單， `private`， `firstprivate`，以及`lastprivate`子句 \([區段 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) 在頁面上 25\)。  
  
-   在平行區域中的私用變數可以標記為私用一次在巢狀指示詞 \([一節 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) 在頁面上 25\)。  
  
-   `copyprivate`子句會新增。  它提供一項機制使用私用變數，從一個小組成員的值，廣播給其他成員。  它會提供共用的變數會難以 \(例如，在需要不同的變數，每個層級遞迴函式\) 時，使用共用的變數值的替代方法。  `copyprivate`子句只能出現在**單一**指示詞 \([一節 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) 在 32\] 頁面上\)。  
  
-   加入預存時間常式的`omp_get_wtick`和`omp_get_wtime` MPI 常式類似。  這些函式所需的執行牆上的時鐘時間 \([區段 3.3.1](../../parallel/openmp/3-3-1-omp-get-wtime-function.md) 在頁面上 44 和[區段 3.3.2](../../parallel/openmp/3-3-2-omp-get-wtick-function.md) 在 45\] 頁面上\)。  
  
-   已新增一份實作定義的行為在 OpenMP C\/C\+\+ 附錄。  實作都必須定義並記載在這些情況下其行為 \([附錄 e](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md) 在頁面上 97\)。  
  
-   釐清或更正功能，先前 OpenMP API 規格 C\/C\+\+ 中的，做下列變更：  
  
    -   Clarified 的行為的`omp_set_nested`和`omp_set_dynamic`時`omp_in_parallel`傳回非零值則表示未定義 \([區段 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 39，頁面上和[區段 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) 在頁面上 40\)。  
  
    -   Clarified 指示詞的巢狀結構，巢狀的平行使用時 \([一節 2.9](../../parallel/openmp/2-9-directive-nesting.md) 在 33\] 頁面上\)。  
  
    -   鎖定初始化和鎖定解構函式可以呼叫在平行區域 \([區段 3.2.1](../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md) 在 42\] 頁面上和[區段 3.2.2](../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md) 在 42\] 頁面上\)。  
  
    -   已新增新的範例 \([附錄 a](../../parallel/openmp/a-examples.md) 在 51\] 頁面上\)。