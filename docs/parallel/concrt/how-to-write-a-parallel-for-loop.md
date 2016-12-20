---
title: "如何：撰寫 parallel_for 迴圈 | Microsoft Docs"
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
  - "撰寫 parallel_for 迴圈 [並行執行階段]"
  - "parallel_for 函式, 範例"
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
caps.latest.revision: 15
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：撰寫 parallel_for 迴圈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個範例將示範如何使用 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 來計算兩個矩陣的乘積。  
  
## 範例  
 下列範例顯示了 `matrix_multiply` 函式，它會計算兩個平方矩陣的乘積。  
  
 [!code-cpp[concrt-parallel-matrix-multiply#1](../../parallel/concrt/codesnippet/CPP/how-to-write-a-parallel-for-loop_1.cpp)]  
  
## 範例  
 下列範例顯示了 `parallel_matrix_multiply` 函式，它會使用 `parallel_for` 演算法，以平行方式執行外部迴圈。  
  
 [!code-cpp[concrt-parallel-matrix-multiply#2](../../parallel/concrt/codesnippet/CPP/how-to-write-a-parallel-for-loop_2.cpp)]  
  
 這個範例只會平行處理外部迴圈，因為它會執行足夠的工作，以便從平行處理的額外負荷中獲益。  如果您平行處理內部迴圈，就無法提升效能，因為內部迴圈所執行的少量工作不會克服平行處理的額外負荷。  因此，在大部分的系統上，僅平行處理外部迴圈是充分發揮並行優勢的最佳途徑。  
  
## 範例  
 下列更完整的範例會比較 `matrix_multiply` 函式與 `parallel_matrix_multiply` 函式之間的效能差異。  
  
 [!code-cpp[concrt-parallel-matrix-multiply#3](../../parallel/concrt/codesnippet/CPP/how-to-write-a-parallel-for-loop_3.cpp)]  
  
 下列是針對配備四個處理器之電腦的範例輸出。  
  
  **連續: 3853**  
**平行: 1311**   
## 編譯程式碼  
 若要編譯程式碼，請複製該程式碼，然後將它貼入 Visual Studio 專案中，或貼入名為 `parallel-matrix-multiply.cpp` 的檔案，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc parallel\-matrix\-multiply.cpp**  
  
## 請參閱  
 [平行演算法](../../parallel/concrt/parallel-algorithms.md)   
 [parallel\_for 函式](../Topic/parallel_for%20Function.md)