---
title: "如何：轉換使用削減變數的 OpenMP 迴圈來使用並行執行階段 | Microsoft Docs"
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
  - "從 OpenMP 轉換為並行執行階段，削減變數"
  - "削減變數，從 OpenMP 轉換為並行執行階段"
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
caps.latest.revision: 13
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：轉換使用削減變數的 OpenMP 迴圈來使用並行執行階段
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個範例示範如何將使用 [reduction](../../parallel/openmp/reference/reduction.md) 子句的 OpenMP [parallel](../../parallel/openmp/reference/parallel.md) [for](../../parallel/openmp/reference/for-openmp.md) 迴圈，轉換為使用並行執行階段。  
  
 OpenMP `reduction` 子句可讓您在平行區域末端指定一個或多個執行削減作業的執行緒私用變數。  OpenMP 預先定義一組削減運算子。  每個削減變數都必須是純量 \(例如 `int`、`long` 和 `float`\)。  OpenMP 也定義平行區域中削減變數用法的數個限制。  
  
 平行模式程式庫 \(PPL\) 提供了 [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) 類別，這個類別提供可重複使用的執行緒區域儲存區，可讓您執行細部計算，然後將這些計算合併成最終的結果。  `combinable` 類別是作用於純量和複雜型別的範本。  若要使用 `combinable` 類別，請在平行建構主體中執行子運算，然後呼叫 [concurrency::combinable::combine](../Topic/combinable::combine%20Method.md) 或 [concurrency::combinable::combine\_each](../Topic/combinable::combine_each%20Method.md) 方法產生最終的結果。  每個 `combine` 和 `combine_each` 方法都會接受「*Combine 函式*」\(Combine Function\)，以指定每組項目的結合方式。  因此，`combinable` 類別不限於一組固定的削減運算子。  
  
## 範例  
 這個範例使用 OpenMP 和並行執行階段，計算前 35 個 Fibonacci 數字的總和。  
  
 [!code-cpp[concrt-openmp#7](../../parallel/concrt/codesnippet/CPP/convert-an-openmp-loop-that-uses-a-reduction-variable_1.cpp)]  
  
 這個範例產生下列輸出。  
  
  **Using OpenMP...**  
**前 35 個 Fibonacci 數字的總和是 14930351。**  
**使用並行執行階段...**  
**前 35 個 Fibonacci 數字的總和是 14930351。** 如需 `combinable` 類別的詳細資訊，請參閱 [平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## 編譯程式碼  
 請複製範例程式碼並將它貼在 Visual Studio 專案中，或是貼在名為  `concrt-omp-fibonacci-reduction.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc \/openmp concrt\-omp\-fibonacci\-reduction.cpp**  
  
## 請參閱  
 [從 OpenMP 移轉至並行執行階段](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)