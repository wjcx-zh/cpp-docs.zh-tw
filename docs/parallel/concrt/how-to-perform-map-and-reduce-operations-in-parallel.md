---
title: "如何：平行執行對應和縮減作業 | Microsoft Docs"
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
  - "parallel_transform 函式範例"
  - "平行對應和縮減，範例"
  - "parallel_reduce 函式範例"
ms.assetid: 9d19fac0-4ab6-4380-a375-3b18eeb87720
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：平行執行對應和縮減作業
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個範例示範如何使用 [parallel_transform](../Topic/parallel_transform%20Function.md) 和 [concurrency::parallel_reduce](../Topic/parallel_reduce%20Function.md) 演算法和 [concurrency::concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) 類別檔中字詞的出現次數。  
  
 A *對應* 作業適用於每個值序列中的函式。 A *減少* 作業會結合為一個值序列的項目。 您可以使用 Standard Template Library (STL) [std::transform](../Topic/transform.md)[std::accumulate](../Topic/accumulate.md) 類別來執行對應和縮減作業。 不過，若要針對許多問題改善效能，您可以使用 `parallel_transform` 演算法以平行方式執行對應作業，以及使用 `parallel_reduce` 演算法以平行方式執行縮減作業。 在某些情況下，您可以使用 `concurrent_unordered_map` 在一個作業中執行對應和縮減。  
  
## <a name="example"></a>範例  
 下列範例會計算文字在檔案中的出現次數。 它會使用 [std:: vector](../../standard-library/vector-class.md) 來表示兩個檔案的內容。 對應作業會計算每個向量中每個字的出現次數。 縮減作業會累計兩個向量的字數統計。  
  
 [!code-cpp[concrt-parallel-map-reduce#1](../../parallel/concrt/codesnippet/CPP/how-to-perform-map-and-reduce-operations-in-parallel_1.cpp)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯程式碼，將它複製然後貼在 Visual Studio 專案中，或貼入名為的檔案 `parallel-map-reduce.cpp` ，然後在 Visual Studio 命令提示字元] 視窗中執行下列命令。  
  
 **cl.exe /EHsc 平行對應 reduce.cpp**  
  
## <a name="robust-programming"></a>穩固程式設計  
 在這個範例中，您可以使用在 concurrent_unordered_map.h中定義的 `concurrent_unordered_map` 類別，在一個作業中執行對應和縮減。  
  
 [!code-cpp[concrt-parallel-map-reduce#2](../../parallel/concrt/codesnippet/CPP/how-to-perform-map-and-reduce-operations-in-parallel_2.cpp)]  
  
 一般而言，您只會平行處理外部或內部迴圈。 如果您的檔案數相當少，而且每個檔案包含許多單字，則請平行處理內部迴圈。 如果您的檔案數相當多，而且每個檔案包含少數單字，則請平行處理外部迴圈。  
  
## <a name="see-also"></a>另請參閱  
 [平行演算法](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_transform 函式](../Topic/parallel_transform%20Function.md)   
 [parallel_reduce 函式](../Topic/parallel_reduce%20Function.md)   
 [concurrent_unordered_map 類別](../../parallel/concrt/reference/concurrent-unordered-map-class.md)
