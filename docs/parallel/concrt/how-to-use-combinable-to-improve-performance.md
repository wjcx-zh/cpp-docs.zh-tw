---
title: "如何：使用可組合的類別改善效能 | Microsoft Docs"
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
helpviewer_keywords: 
  - "combinable 類別，範例"
  - "使用 combinable 改善平行效能 [並行執行階段]"
ms.assetid: fa730580-1c94-4b2d-8aec-57c91dc0497e
caps.latest.revision: 17
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用可組合的類別改善效能
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個範例將示範如何使用 [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) 類別來計算 [std::array](../../standard-library/array-class-stl.md) 物件中屬於質數的數字總和。  `combinable` 類別會透過排除共用狀態，改善效能。  
  
> [!TIP]
>  在某些情況下，平行對應 \([concurrency::parallel\_transform](../Topic/parallel_transform%20Function.md)\) 和減少 \([並行::parallel\_reduce](../Topic/parallel_reduce%20Function.md)\) 可以在 `combinable`中提供效能改善。  如需使用對應並減少作業產生的結果和這個範例相同的範例，請參閱 [平行演算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## 範例  
 下列範例會使用 [std::accumulate](../Topic/accumulate.md) 函式來計算陣列中屬於質數的元素總和。  在這個範例中，`a` 是 `array` 物件，而且 `is_prime` 函式會判斷其輸入值是否為質數。  
  
 [!code-cpp[concrt-parallel-sum-of-primes#1](../../parallel/concrt/codesnippet/CPP/how-to-use-combinable-to-improve-performance_1.cpp)]  
  
## 範例  
 下列範例顯示平行處理上一則範例的自然方式。  這個範例會使用 [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md) 演算法，以平行方式處理陣列，並且使用 [concurrency::critical\_section](../../parallel/concrt/reference/critical-section-class.md) 物件來同步處理 `prime_sum` 變數的存取權。  這個範例不會調整，因為每個執行緒都必須等候共用資源成為可用。  
  
 [!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/CPP/how-to-use-combinable-to-improve-performance_2.cpp)]  
  
## 範例  
 下列範例會使用 `combinable` 物件來改善上一則範例的效能。  這個範例會排除同步處理物件的需求。它會進行調整，因為 `combinable` 物件可讓每個執行緒獨立執行其工作。  
  
 `combinable` 物件通常會用於兩個步驟中。  首先，以平行方式執行工作，藉以產生一連串精細的運算。  接著，將運算結合 \(或減少\) 成最終結果。  這個範例會使用 [concurrency::combinable::local](../Topic/combinable::local%20Method.md) 方法來取得區域總和的參考。  然後，它會使用 [concurrency::combinable::combine](../Topic/combinable::combine%20Method.md) 方法和 [std::plus](../../standard-library/plus-struct.md) 物件，將這些區域運算結合成最終結果。  
  
 [!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/CPP/how-to-use-combinable-to-improve-performance_3.cpp)]  
  
## 範例  
 下列範例會同時以循序和平行方式計算質數的總和。  此範例會將執行這兩個運算所需的時間列印至主控台。  
  
 [!code-cpp[concrt-parallel-sum-of-primes#4](../../parallel/concrt/codesnippet/CPP/how-to-use-combinable-to-improve-performance_4.cpp)]  
  
 下列是針對配備四個處理器之電腦的範例輸出。  
  
  **1709600813**  
**循序的時間:6178 毫秒**  
**1709600813**  
**平行時間:1638 毫秒**   
## 編譯程式碼  
 若要編譯程式碼，請複製該程式碼，然後將它貼入 Visual Studio 專案中，或貼入名為  `parallel-sum-of-primes.cpp` 的檔案，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc parallel\-sum\-of\-primes.cpp**  
  
## 穩固程式設計  
 如需使用對應並減少作業會產生相同的結果的範例，請參閱 [平行演算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## 請參閱  
 [平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)   
 [combinable 類別](../../parallel/concrt/reference/combinable-class.md)   
 [critical\_section 類別](../../parallel/concrt/reference/critical-section-class.md)