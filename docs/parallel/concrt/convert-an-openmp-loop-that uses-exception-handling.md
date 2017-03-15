---
title: "如何：轉換使用例外狀況處理的 OpenMP 迴圈來使用並行執行階段 | Microsoft Docs"
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
  - "例外狀況處理, 從 OpenMP 轉換為並行執行階段"
  - "從 OpenMP 轉換為並行執行階段, 例外狀況處理"
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：轉換使用例外狀況處理的 OpenMP 迴圈來使用並行執行階段
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個範例示範如何轉換執行例外狀況處理的 OpenMP [parallel](../../parallel/openmp/reference/parallel.md) [for](../../parallel/openmp/reference/for-openmp.md) 迴圈，以使用並行執行階段例外狀況處理機制。  
  
 在 OpenMP 中，在平行區域中擲回的例外狀況必須在相同區域中由相同執行緒攔截及處理。  逸出平行區域的例外狀況是由未處理例外處理常式攔截，該處理常式預設會結束處理序。  
  
 在並行執行階段中，當您在傳遞給工作群組 \(例如 [concurrency::task\_group](../Topic/task_group%20Class.md) 或 [concurrency::structured\_task\_group](../../parallel/concrt/reference/structured-task-group-class.md) 物件\) 或平行演算法 \(例如 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md)\) 的工作函式主體中擲回例外狀況時，執行階段會儲存該例外狀況，並將它封送處理至等待工作群組或演算法完成的內容。  若為工作群組，等待的內容為呼叫 [concurrency::task\_group::wait](../Topic/task_group::wait%20Method.md)、[concurrency::structured\_task\_group::wait](../Topic/structured_task_group::wait%20Method.md)、[concurrency::task\_group::run\_and\_wait](../Topic/task_group::run_and_wait%20Method.md) 或 [concurrency::structured\_task\_group::run\_and\_wait](../Topic/structured_task_group::run_and_wait%20Method.md) 的內容。  若為平行演算法，等待的內容為呼叫該演算法的內容。  執行階段也會停止工作群組中的所有作用中工作 \(包括子工作群組中的工作\)，並捨棄任何尚未啟動的工作。  
  
## 範例  
 這個範例示範如何處理 OpenMP `parallel` 區域中和 `parallel_for` 呼叫中的例外狀況。  `do_work` 函式會執行未成功並因而擲回 [std::bad\_alloc](../../standard-library/bad-alloc-class.md) 型別例外狀況的記憶體配置要求。  在使用 OpenMP 的版本中，擲回例外狀況的執行緒也必須攔截該例外狀況。  換句話中，OpenMP 平行迴圈的每個反覆項目都必須處理例外狀況。  在使用並行執行階段的版本中，主要執行緒會攔截其他執行緒擲回的例外狀況。  
  
 [!code-cpp[concrt-openmp#3](../../parallel/concrt/codesnippet/CPP/convert-an-openmp-loop-that uses-exception-handling_1.cpp)]  
  
 這個範例產生下列輸出。  
  
  **Using OpenMP...**  
**An error of type 'class std::bad\_alloc' occurred.**  
**An error of type 'class std::bad\_alloc' occurred.**  
**An error of type 'class std::bad\_alloc' occurred.**  
**An error of type 'class std::bad\_alloc' occurred.**  
**An error of type 'class std::bad\_alloc' occurred.**  
**An error of type 'class std::bad\_alloc' occurred.**  
**An error of type 'class std::bad\_alloc' occurred.**  
**An error of type 'class std::bad\_alloc' occurred.**  
**An error of type 'class std::bad\_alloc' occurred.**  
**An error of type 'class std::bad\_alloc' occurred.**  
**Using the Concurrency Runtime...**  
**An error of type 'class std::bad\_alloc' occurred.** 在這個使用 OpenMP 的範例版本中，例外狀況會在每個迴圈反覆項目中發生並加以處理。  在使用並行執行階段的版本中，執行階段會儲存例外狀況、停止所有作用中工作、捨棄任何尚未啟動的工作，以及將例外狀況封送處理置呼叫 `parallel_for` 的內容。  
  
 如果您需要使用 OpenMP 的版本在例外狀況發生之後結束，可以使用 Boolean 旗標對發生錯誤的其他迴圈反覆項目發出信號。  如 [如何：轉換使用取消的 OpenMP 迴圈來使用並行執行階段](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)主題的範例所示，如果設定了旗標，後續迴圈反覆項目就不會執行任何動作。  相反地，如果您需要使用並行執行階段的迴圈在例外狀況發生之後繼續進行，請在平行迴圈主體本身內處理例外狀況。  
  
 並行執行階段的其他元件 \(例如非同步代理程式和輕量型工作\) 不會傳輸例外狀況。  而未處理例外狀況是由未處理例外處理常式攔截，而該處理常式預設會結束處理序。  如需例外狀況處理的詳細資訊，請參閱[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。  
  
 如需 `parallel_for` 和其他平行演算法的詳細資訊，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## 編譯程式碼  
 請複製範例程式碼並將它貼在 Visual Studio 專案中，或是貼在名為 `concrt-omp-exceptions.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc \/openmp concrt\-omp\-exceptions.cpp**  
  
## 請參閱  
 [從 OpenMP 移轉至並行執行階段](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [平行演算法](../../parallel/concrt/parallel-algorithms.md)