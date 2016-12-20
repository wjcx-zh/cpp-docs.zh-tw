---
title: "如何：使用例外狀況處理來中斷平行迴圈 | Microsoft Docs"
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
  - "搜尋演算法, 撰寫 [並行執行階段]"
  - "撰寫搜尋演算法 [並行執行階段]"
ms.assetid: 16d7278c-2d10-4014-9f58-f1899e719ff9
caps.latest.revision: 15
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用例外狀況處理來中斷平行迴圈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題說明如何針對基本的樹狀結構撰寫搜尋演算法。  
  
 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)主題說明取消動作在平行模式程式庫中的角色。  比起用 [concurrency::task\_group::cancel](../Topic/task_group::cancel%20Method.md) 和 [concurrency::structured\_task\_group::cancel](../Topic/structured_task_group::cancel%20Method.md) 方法，用例外狀況處理來取消平行工作比較沒有效率。  不過，一種適合使用例外狀況處理來取消工作的案例是，當您呼叫會使用工作或平行演算法但未提供可取消之 `task_group` 或 `structured_task_group` 物件的協力廠商程式庫。  
  
## 範例  
 下列範例顯示基本的 `tree` 型別，這個型別包含一個資料項目和一份子節點清單。  下列各節顯示 `for_all` 方法的主體，該方法會以遞迴方式在每個子節點上執行工作函式。  
  
 [!code-cpp[concrt-task-tree-search#2](../../parallel/concrt/codesnippet/CPP/how-to-use-exception-handling-to-break-from-a-parallel-loop_1.cpp)]  
  
## 範例  
 下列範例顯示 `for_all` 方法。  這個方法會使用 [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md) 演算法，以平行方式在樹狀結構的每個節點上執行工作函式。  
  
 [!code-cpp[concrt-task-tree-search#1](../../parallel/concrt/codesnippet/CPP/how-to-use-exception-handling-to-break-from-a-parallel-loop_2.cpp)]  
  
## 範例  
 下列範例顯示 `search_for_value` 函式，這個函式會在提供的 `tree` 物件中搜尋值。  這個函式會傳遞工作函式給 `for_all` 方法，該函式會在發現有樹狀節點包含所提供的值時擲回例外狀況。  
  
 假設 `tree` 類別是由協力廠商程式庫所提供，而且您無法變更它。  在此情況下，適合使用例外狀況處理，因為 `for_all` 方法未提供 `task_group` 或 `structured_task_group` 物件給呼叫端。  因此，工作函式無法直接取消其父工作群組。  
  
 當您提供給工作群組的工作函式擲回例外狀況時，執行階段會停止工作群組中的所有工作 \(包括任何子工作群組\)，並且捨棄任何尚未開始的工作。  `search_for_value` 函式會使用 `try`\-`catch` 區塊來擷取例外狀況並將結果列印至主控台。  
  
 [!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/CPP/how-to-use-exception-handling-to-break-from-a-parallel-loop_3.cpp)]  
  
## 範例  
 下列範例會建立 `tree` 物件並以平行方式在其中搜尋數個值。  本主題稍後會說明 `build_tree` 函式。  
  
 [!code-cpp[concrt-task-tree-search#4](../../parallel/concrt/codesnippet/CPP/how-to-use-exception-handling-to-break-from-a-parallel-loop_4.cpp)]  
  
 這個範例會使用 [concurrency::parallel\_invoke](../Topic/parallel_invoke%20Function.md) 演算法以平行方式搜尋值。  如需這個演算法的詳細資訊，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## 範例  
 下列完整範例會使用例外狀況處理來搜尋基本樹狀結構中的值。  
  
 [!code-cpp[concrt-task-tree-search#5](../../parallel/concrt/codesnippet/CPP/how-to-use-exception-handling-to-break-from-a-parallel-loop_5.cpp)]  
  
 這個範例 \(Example\) 產生下列範例 \(Sample\) 輸出。  
  
  **Found a node with value 32614.**  
**Found a node with value 86131.**  
**Did not find node with value 17522.**   
## 編譯程式碼  
 請複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼在名為 `task-tree-search.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc task\-tree\-search.cpp**  
  
## 請參閱  
 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [平行演算法](../../parallel/concrt/parallel-algorithms.md)   
 [task\_group 類別](../Topic/task_group%20Class.md)   
 [structured\_task\_group 類別](../../parallel/concrt/reference/structured-task-group-class.md)   
 [parallel\_for\_each 函式](../Topic/parallel_for_each%20Function.md)