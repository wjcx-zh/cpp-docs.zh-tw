---
title: "如何：使用 parallel_invoke 執行平行作業 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "parallel_invoke 函式, 範例"
  - "以平行方式呼叫多個函式 [並行執行階段]"
ms.assetid: a6aea69b-d647-4b7e-bf3b-e6a6a9880072
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# 如何：使用 parallel_invoke 執行平行作業
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個範例示範如何使用 [concurrency::parallel\_invoke](../Topic/parallel_invoke%20Function.md) 演算法，改善對共用資料來源執行多個作業的程式效能。  因為沒有作業會修改來源，因此可以直接平行執行這些作業。  
  
## 範例  
 在下列程式碼範例中，會建立 `MyDataType` 型別的變數，呼叫函式以初始化該變數，然後在該資料上執行多個冗長作業。  
  
 [!code-cpp[concrt-parallel-word-mining#1](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-execute-parallel-operations_1.cpp)]  
  
 如果 `lengthy_operation1`、`lengthy_operation2` 和 `lengthy_operation3` 函式未修改 `MyDataType` 變數，這些函式可以平行執行，不需要其他修改。  
  
## 範例  
 下列範例修改上述範例以平行執行。  `parallel_invoke` 演算法平行執行每項工作，然後在所有工作都完成後傳回。  
  
 [!code-cpp[concrt-parallel-word-mining#2](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-execute-parallel-operations_2.cpp)]  
  
## 範例  
 下列範例會從 gutenberg.org 下載荷馬所著的《伊里亞德》\(*The Iliad*\)，然後對該檔案執行多個作業。  此範例會先循序執行這些作業，然後再以平行方式執行相同作業。  
  
 [!code-cpp[concrt-parallel-word-mining#3](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-execute-parallel-operations_3.cpp)]  
  
 這個範例 \(Example\) 產生下列範例 \(Sample\) 輸出。  
  
  **下載 'The Iliad'...**  
**執行循序版本… 跑了 953 毫秒。**  
**執行平行版本... 跑了 656 毫秒。**  
**有五個或多個字母的最常見的文字是:**  
 **their \(953\)**  
 **shall \(444\)。**  
 **which \(431\)**  
 **great \(398\)**  
 **Hector \(349\)**  
 **Achilles \(309\)**  
 **through \(301\)**  
 **these \(268\)**  
 **chief \(259\)**  
**有相同的第一個字母文字的最長序列如下:**  
 **through the tempest to the tented**  
**下列為出現的回文文字:**  
 **spots stops**  
 **speed deeps**  
 **keels sleek** 這個範例使用 `parallel_invoke` 演算法，呼叫多個可作用於相同資料來源的函式。  您可以使用 `parallel_invoke` 演算法，平行呼叫任何一組函式，而不只是作用於相同資料的這些函式。  
  
 因為 `parallel_invoke` 演算法會以平行方式呼叫每個工作函式，所以其效能會受到花費最長時間來完成的函式所限制 \(也就是說，如果執行階段會在個別處理器上處理每個函式的話\)。  如果這個範例以平行方式執行的工作比可用的處理器數目更多，每個處理器可能會執行多項工作。  在此情況下，效能會受到花費最長時間來完成的工作群組所限制。  
  
 因為這個範例平行執行三個作業，在具有三個以上處理器的電腦，您應該不預期效能延展。  若要改善效能，您可以將長時間執行的工作細分為較小的工作並平行執行這些工作。  
  
 如果不需要支援取消，請使用 `parallel_invoke` 演算法代替 [concurrency::task\_group](../Topic/task_group%20Class.md) 和 [concurrency::structured\_task\_group](../../parallel/concrt/reference/structured-task-group-class.md) 類別。  如需比較 `parallel_invoke` 演算法與工作群組用法的範例，請參閱[如何：使用 parallel\_invoke 撰寫平行排序常式](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)。  
  
## 編譯程式碼  
 若要編譯程式碼，請複製該程式碼，然後將它貼入 Visual Studio 專案中，或貼入名為 `parallel-word-mining.cpp` 的檔案，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc \/MD \/DUNICODE \/D\_AFXDLL parallel\-word\-mining.cpp**  
  
## 請參閱  
 [平行演算法](../../parallel/concrt/parallel-algorithms.md)   
 [parallel\_invoke 函式](../Topic/parallel_invoke%20Function.md)