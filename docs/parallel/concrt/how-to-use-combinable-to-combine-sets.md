---
title: "如何：使用可組合的類別結合集合 | Microsoft Docs"
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
  - "combinable 類別，範例"
  - "使用 combinable 結合集合 [並行執行階段]"
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用可組合的類別結合集合
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題將示範如何使用 [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) 類別來計算一組質數。  
  
## 範例  
 下列範例會計算一組質數兩次。  每次計算都會將結果儲存在 [std::bitset](../../standard-library/bitset-class.md) 物件中。  此範例會先循序計算這個集合，然後再以平行方式計算這個集合。  範例也會將執行這兩個計算的所需時間列印至主控台。  
  
 此範例會使用 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 演算法和 `combinable` 物件來產生執行緒區域集合。  然後，它會使用 [concurrency::combinable::combine\_each](../Topic/combinable::combine_each%20Method.md) 方法將這些執行緒區域集合結合成最終集合。  
  
 [!code-cpp[concrt-parallel-combine-primes#1](../../parallel/concrt/codesnippet/CPP/how-to-use-combinable-to-combine-sets_1.cpp)]  
  
 下列是針對配備四個處理器之電腦的範例輸出。  
  
  **循序的時間:312 毫秒**  
**平行時間:78 毫秒**   
## 編譯程式碼  
 請複製範例程式碼並將它貼在 Visual Studio 專案中，或是貼在名為 `parallel-combine-primes.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc parallel\-combine\-primes.cpp**  
  
## 請參閱  
 [平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)   
 [combinable 類別](../../parallel/concrt/reference/combinable-class.md)   
 [combinable::combine\_each 方法](../Topic/combinable::combine_each%20Method.md)