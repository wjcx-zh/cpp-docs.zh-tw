---
title: "如何：撰寫 parallel_for_each 迴圈 | Microsoft Docs"
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
  - "撰寫 parallel_for_each 迴圈 [並行執行階段]"
  - "parallel_for_each 函式，範例"
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
caps.latest.revision: 15
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：撰寫 parallel_for_each 迴圈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個範例將示範如何使用 [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md) 演算法，以平行方式計算 [std::array](../../standard-library/array-class-stl.md) 物件中質數的計數。  
  
## 範例  
 下列範例會計算陣列中質數的計數兩次。  此範例會先使用 [std::for\_each](../Topic/for_each.md) 演算法來循序計算計數。  然後，此範例會使用 `parallel_for_each` 演算法，以平行方式執行相同的工作。  範例也會將執行這兩個計算的所需時間列印至主控台。  
  
 [!code-cpp[concrt-parallel-count-primes#1](../../parallel/concrt/codesnippet/CPP/how-to-write-a-parallel-for-each-loop_1.cpp)]  
  
 下列是針對配備四個處理器之電腦的範例輸出。  
  
  **循序版本:**  
**找到 17984 個質數**  
**採用 6115 毫秒**  
**平行版本:**  
**找到 17984 個質數**  
**用了 1653 毫秒**   
## 編譯程式碼  
 若要編譯程式碼，請複製該程式碼，然後將它貼入 Visual Studio 專案中，或貼入名為 `parallel-count-primes.cpp` 的檔案，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc parallel\-count\-primes.cpp**  
  
## 穩固程式設計  
 此範例傳遞給 `parallel_for_each` 演算法的 Lambda 運算式會使用 `InterlockedIncrement` 函式來啟用迴圈的平行反覆項目，以便同時遞增計數器。  如果您使用 `InterlockedIncrement` 等函式來同步處理共用資源的存取權，可能會在您的程式碼中呈現效能瓶頸。  您可以使用無鎖定同步處理機制 \(例如 [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) 類別\) 來排除共用資源的同時存取。  如需以這種方式使用 `combinable` 類別的範例，請參閱 [如何：使用可組合的類別改善效能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)。  
  
## 請參閱  
 [平行演算法](../../parallel/concrt/parallel-algorithms.md)   
 [parallel\_for\_each 函式](../Topic/parallel_for_each%20Function.md)