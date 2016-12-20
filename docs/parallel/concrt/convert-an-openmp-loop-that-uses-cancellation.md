---
title: "如何：轉換使用取消的 OpenMP 迴圈來使用並行執行階段 | Microsoft Docs"
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
  - "從 OpenMP 轉換為並行執行階段，取消"
  - "取消，從 OpenMP 轉換為並行執行階段"
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：轉換使用取消的 OpenMP 迴圈來使用並行執行階段
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

某些平行迴圈不需要所有反覆項目都執行。  例如，搜尋值的演算法可以在找到值後終止。  OpenMP 未提供中斷平行迴圈的機制。  不過，您可以使用布林值 \(或旗標\)，讓迴圈反覆項目表示已找到解決方案。  並行執行階段提供可讓某個工作取消其他尚未啟動之工作的功能。  
  
 這個範例示範如何將不需要所有反覆項目執行的 OpenMP [parallel](../../parallel/openmp/reference/parallel.md) [for](../../parallel/openmp/reference/for-openmp.md) 迴圈，轉換為使用並行執行階段取消機制。  
  
## 範例  
 這個範例使用 OpenMP 和並行執行階段，實作 [std::any\_of](../Topic/any_of.md) 演算法的平行版本。  此範例的 OpenMP 版本使用旗標，在所有平行迴圈反覆項目之間表示已符合條件。  使用並行執行階段的版本使用 [concurrency::structured\_task\_group::cancel](../Topic/structured_task_group::cancel%20Method.md) 方法，在符合條件時停止整體作業。  
  
 [!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/CPP/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]  
  
 這個範例產生下列輸出。  
  
  **Using OpenMP...**  
**9114046 is in the array.**  
**Using the Concurrency Runtime...**  
**9114046 is in the array.** 在使用 OpenMP 的版本中，即使設定旗標時，迴圈的所有反覆項目都會執行。  此外，如果工作有任何子工作，旗標也必須用於這些子工作，以溝通取消。  在並行執行階段中，當工作群組取消時，執行階段會取消整個工作樹狀結構，包括子工作。  [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md) 演算法會使用工作來執行迴圈反覆項目。  因此，當一個迴圈反覆項目取消根工作時，整個計算樹狀結構也會被取消。  取消工作樹狀結構時，執行階段不會啟動新的工作。  不過，執行階段允許已啟動的工作完成。  因此，在 `parallel_for_each` 演算法的案例中，使用中迴圈反覆項目可以清除其資源。  
  
 在這個範例的兩個版本中，如果陣列包含一個以上要搜尋的值複本，多個迴圈反覆項目可以同時設定結果及取消整體作業。  如果您的問題需要在符合條件時只讓一個工作執行，可以使用同步處理基本型別，例如關鍵區段。  
  
 您也可以使用例外狀況處理，取消使用 PPL 的工作。  如需取消的詳細資訊，請參閱 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)。  
  
 如需 `parallel_for_each` 和其他平行演算法的詳細資訊，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## 編譯程式碼  
 請複製範例程式碼並將它貼在 Visual Studio 專案中，或是貼在名為 `concrt-omp-parallel-any-of.cp`p 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc \/openmp concrt\-omp\-parallel\-any\-of.cpp**  
  
## 請參閱  
 [從 OpenMP 移轉至並行執行階段](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [平行演算法](../../parallel/concrt/parallel-algorithms.md)