---
title: "如何：使用 parallel_invoke 撰寫平行排序常式 | Microsoft Docs"
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
  - "task_handle 類別, 範例"
  - "task_group 類別, 範例"
  - "make_task 函式, 範例"
  - "structured_task_group 類別, 範例"
  - "使用工作群組改善平行效能 [並行執行階段]"
ms.assetid: 53979a2a-525d-4437-8952-f1ff85b37673
caps.latest.revision: 23
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 parallel_invoke 撰寫平行排序常式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件說明如何使用 [parallel\_invoke](../Topic/parallel_invoke%20Function.md) 演算法改善雙調排序演算法的效能。  雙調排序演算法會以遞迴方式將輸入序列分割成較小的已排序資料分割。  因為每個分割作業都與所有其他作業無關，所以雙調排序演算法可以以平行方式執行。  
  
 雖然雙調排序是一種會將所有輸入序列組合排序的「*排序網路*」\(Sorting Network\)，但是它會將長度為 2 的次方的序列排序。  
  
> [!NOTE]
>  這個範例說明使用平行排序常式。  您也可以使用內建排序 PPL 所提供之演算法: [concurrency::parallel\_sort](../Topic/parallel_sort%20Function.md)、 [concurrency::parallel\_buffered\_sort](../Topic/parallel_buffered_sort%20Function.md)和 [concurrency::parallel\_radixsort](../Topic/parallel_radixsort%20Function.md)。  如需詳細資訊，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。  
  
##  <a name="top"></a> 章節  
 本文件將說明下列工作：  
  
-   [以循序方式執行雙調排序](#serial)  
  
-   [使用 parallel\_invoke 以平行方式執行雙調排序](#parallel)  
  
##  <a name="serial"></a> 以循序方式執行雙調排序  
 下列範例顯示雙調排序演算法的循序版本。  `bitonic_sort` 函式會將序列分割成兩個資料分割，並將這些資料分割反向排序，然後合併結果。  這個函式會以遞迴方式呼叫自己兩次，來將每個資料分割排序。  
  
 [!code-cpp[concrt-parallel-bitonic-sort#1](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_1.cpp)]  
  
 \[[上方](#top)\]  
  
##  <a name="parallel"></a> 使用 parallel\_invoke 以平行方式執行雙調排序  
 本節說明如何使用 `parallel_invoke` 演算法來平行執行雙調排序演算法。  
  
### 程序  
  
##### 若要以平行方式執行雙調排序演算法  
  
1.  加入標頭檔 ppl.h 的 `#include` 指示詞。  
  
     [!code-cpp[concrt-parallel-bitonic-sort#10](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_2.cpp)]  
  
2.  加入 `concurrency` 命名空間的 `using` 指示詞。  
  
     [!code-cpp[concrt-parallel-bitonic-sort#11](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_3.cpp)]  
  
3.  建立名為 `parallel_bitonic_mege` 的函式，這個函式會在有足夠的工作量時使用 `parallel_invoke` 演算法平行合併序列。  否則呼叫 `bitonic_merge`，循序合併序列。  
  
     [!code-cpp[concrt-parallel-bitonic-sort#2](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_4.cpp)]  
  
4.  使用 `bitonic_sort` 函式，執行與前述步驟類似的程序。  
  
     [!code-cpp[concrt-parallel-bitonic-sort#3](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_5.cpp)]  
  
5.  建立 `parallel_bitonic_sort` 函式的多載版本，依遞增順序排序陣列。  
  
     [!code-cpp[concrt-parallel-bitonic-sort#4](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_6.cpp)]  
  
 `parallel_invoke` 演算法會在呼叫端內容上執行最後一個工作序列，以減少額外負荷。  例如，在 `parallel_bitonic_sort` 函式中，第一個工作會在個別內容上執行，而第二個工作會在呼叫端內容上執行。  
  
 [!code-cpp[concrt-parallel-bitonic-sort#5](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_7.cpp)]  
  
 下列完整範例會執行雙調排序演算法的循序和平行版本。  這個範例也會將每個計算需要的執行時間列印至主控台。  
  
 [!code-cpp[concrt-parallel-bitonic-sort#8](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_8.cpp)]  
  
 下列是針對配備四個處理器之電腦的範例輸出。  
  
  **serial time: 4353**  
**parallel time: 1248** \[[上方](#top)\]  
  
## 編譯程式碼  
 若要編譯程式碼，請複製該程式碼，然後將它貼在 Visual Studio 專案中，或貼在名為 `parallel-bitonic-sort.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc parallel\-bitonic\-sort.cpp**  
  
## 健全的程式設計  
 這個範例會使用 `parallel_invoke` 演算法而不是 [concurrency::task\_group](../Topic/task_group%20Class.md) 類別，因為每個工作群組的存留期都不會比函式長。  建議您盡量使用 `parallel_invoke`，因為它的執行額外負荷小於 `task group` 物件，因此可讓您撰寫執行效果更佳的程式碼。  
  
 有些演算法的平行版本只有在有足夠的工作要執行時，才會有較佳的執行效果。  例如，如果序列中有 500 個以下的項目，則 `parallel_bitonic_merge` 函式會呼叫 `bitonic_merge` 這個循序版本。  您也可以根據工作量來規劃整體排序策略。  例如，如果陣列包含少於 500 個項目，使用快速排序演算法的循序版本可能更有效率，如下列範例所示：  
  
 [!code-cpp[concrt-parallel-bitonic-sort#9](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_9.cpp)]  
  
 如同任何平行演算法，建議您適當地進行程式碼剖析和微調。  
  
## 請參閱  
 [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [parallel\_invoke 函式](../Topic/parallel_invoke%20Function.md)