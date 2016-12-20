---
title: "如何：轉換 OpenMP parallel for 迴圈來使用並行執行階段 | Microsoft Docs"
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
  - "從 OpenMP 轉換為並行執行階段，parallel for 迴圈"
  - "從 OpenMP 轉換為並行執行階段，平行迴圈"
  - "parallel for 迴圈，從 OpenMP 轉換為並行執行階段"
  - "平行迴圈，從 OpenMP 轉換為並行執行階段"
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
caps.latest.revision: 13
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：轉換 OpenMP parallel for 迴圈來使用並行執行階段
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個範例示範如何將使用 OpenMP [parallel](../../parallel/openmp/reference/parallel.md) 和 [for](../../parallel/openmp/reference/for-openmp.md) 指示詞的基本迴圈，轉換為使用並行執行階段 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 演算法。  
  
## 範例  
 這個範例使用 OpenMP 和並行執行階段，計算隨機值陣列中質數的計數。  
  
 [!code-cpp[concrt-openmp#1](../../parallel/concrt/codesnippet/CPP/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_1.cpp)]  
  
 這個範例產生下列輸出。  
  
  **Using OpenMP...**  
**找到 107254 個質數。**  
**使用並行執行階段...**  
**找到 107254 個質數。** `parallel_for` 演算法和 OpenMP 3.0 允許索引類型為帶正負號的整數類資料型別或不帶正負號的整數類資料型別。  `parallel_for` 演算法也會確定指定的範圍不溢出帶正負號型別。  OpenMP 2.0 和 2.5 版只允許帶正負號的整數索引類型。  OpenMP 也不會驗證索引範圍。  
  
 這個範例中使用並行執行階段的版本也會以 [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) 物件代替 [atomic](../../parallel/openmp/reference/atomic.md) 指示詞，遞增計數器值，而不需要同步處理。  
  
 如需 `parallel_for` 和其他平行演算法的詳細資訊，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。  如需 `combinable` 類別的詳細資訊，請參閱 [平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## 範例  
 這個範例將前述範例修改為作用於 [std::array](../../standard-library/array-class-stl.md) 物件，而不是原生陣列物。  因為 OpenMP 2.0 和 2.5 版在 `parallel` `for` 建構中只允許帶正負號的整數索引類型，所以您不可使用 Iterator 平行存取標準樣板程式庫 \(STL\) 容器中的項目。  平行模式程式庫 \(PPL\) 提供了 [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md) 演算法，這個演算法會以平行方式針對例如 STL 所提供的反覆容器執行工作。  它會使用 `parallel_for` 演算法所使用的相同分割邏輯。  `parallel_for_each` 演算法與 STL [std::for\_each](../Topic/for_each.md) 演算法很相似，不過 `parallel_for_each` 演算法會執行並行工作。  
  
 [!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/CPP/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]  
  
## 編譯程式碼  
 請複製範例程式碼並將它貼在 Visual Studio 專案中，或是貼在名為 `concrt-omp-count-primes.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc \/openmp concrt\-omp\-count\-primes.cpp**  
  
## 請參閱  
 [從 OpenMP 移轉至並行執行階段](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [平行演算法](../../parallel/concrt/parallel-algorithms.md)   
 [平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)