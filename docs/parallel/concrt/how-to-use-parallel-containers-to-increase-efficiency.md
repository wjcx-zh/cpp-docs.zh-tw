---
title: "如何：使用平行容器提高效率 | Microsoft Docs"
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
  - "使用平行容器提高效率 [並行執行階段]"
  - "concurrent_queue 類別，範例"
  - "concurrent_vector 類別，範例"
ms.assetid: bd00046d-e9b6-4ae1-b661-3995f671b867
caps.latest.revision: 13
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用平行容器提高效率
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題將示範如何使用平行容器，以平行方式有效率地儲存和存取資料。  
  
 此範例程式碼會以平行方式計算質數和 Carmichael 數字的集合。  然後，此程式碼會針對每個 Carmichael 數字，計算該數字的質因數。  
  
## 範例  
 下列範例顯示了 `is_prime` 函式 \(它會判斷輸入值是否為質數\) 以及 `is_carmichael` 函式 \(它會判斷輸入值是否為 Carmichael 數字\)。  
  
 [!code-cpp[concrt-carmichael-primes#1](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-containers-to-increase-efficiency_1.cpp)]  
  
## 範例  
 下列範例會使用 `is_prime` 和 `is_carmichael` 函式來計算質數和 Carmichael 數字的集合。  此範例會使用 [concurrency::parallel\_invoke](../Topic/parallel_invoke%20Function.md) 和 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 演算法，以平行方式計算每個集合。  如需平行演算法的詳細資訊，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。  
  
 這個範例會使用 [concurrency::concurrent\_queue](../../parallel/concrt/reference/concurrent-queue-class.md) 物件來保存 Carmichael 數字的集合，因為它之後將使用該物件當做工作佇列。  它會使用 [concurrency::concurrent\_vector](../../parallel/concrt/reference/concurrent-vector-class.md) 物件來保存質數的集合，因為它之後將逐一查看此集合來尋找質因數。  
  
 [!code-cpp[concrt-carmichael-primes#2](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-containers-to-increase-efficiency_2.cpp)]  
  
## 範例  
 下列範例顯示了 `prime_factors_of` 函式，它會使用試除法來尋找給定值的所有質因數。  
  
 此函式會使用 [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md) 演算法來逐一查看質數的集合。  `concurrent_vector` 物件可讓平行迴圈以並行方式將質因數加入至結果。  
  
 [!code-cpp[concrt-carmichael-primes#3](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-containers-to-increase-efficiency_3.cpp)]  
  
## 範例  
 這個範例會透過呼叫 `prime_factors_of` 函式來計算質因數，處理 Carmichael 數字佇列中的每個項目。  它會使用工作群組，以平行方式執行這項工作。  如需工作群組的詳細資訊，請參閱[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
 這個範例會列印每個 Carmichael 數字的質因數 \(如果該數字的質因數超過四個的話\)。  
  
 [!code-cpp[concrt-carmichael-primes#4](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-containers-to-increase-efficiency_4.cpp)]  
  
## 範例  
 下列程式碼顯示了完整的範例，其中使用平行容器來計算 Carmichael 數字的質因數。  
  
 [!code-cpp[concrt-carmichael-primes#5](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-containers-to-increase-efficiency_5.cpp)]  
  
 這個範例 \(Example\) 產生下列範例 \(Sample\) 輸出。  
  
  **9890881 的質因數是:7 11 13 41 241。**  
**825265 的質因數是:5 7 17 19 73。**  
**1050985 的質因數是:5 13 19 23 37。**   
## 編譯程式碼  
 請複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼在名為 `carmichael-primes.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc carmichael\-primes.cpp**  
  
## 請參閱  
 [平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)   
 [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [concurrent\_vector 類別](../../parallel/concrt/reference/concurrent-vector-class.md)   
 [concurrent\_queue 類別](../../parallel/concrt/reference/concurrent-queue-class.md)   
 [parallel\_invoke 函式](../Topic/parallel_invoke%20Function.md)   
 [parallel\_for 函式](../Topic/parallel_for%20Function.md)   
 [task\_group 類別](../Topic/task_group%20Class.md)