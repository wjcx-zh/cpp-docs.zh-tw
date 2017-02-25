---
title: "如何：使用取消來中斷平行迴圈 | Microsoft Docs"
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
  - "平行搜尋演算法, 撰寫 [並行執行階段]"
  - "撰寫平行搜尋演算法 [並行執行階段]"
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# 如何：使用取消來中斷平行迴圈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個範例將示範如何使用取消來實作基礎的平行搜尋演算法。  
  
## 範例  
 下列範例會使用取消來搜尋陣列中的項目。  `parallel_find_any` 函式會使用 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 演算法和 [concurrency::structured\_task\_group](../Topic/run_with_cancellation_token%20Function.md) 函式來搜尋包含給定值的位置。  當平行迴圈中找到此值時，它會呼叫 [concurrency::cancellation\_token\_source::cancel](../Topic/cancellation_token_source::cancel%20Method.md) 方法來取消未來的工作。  
  
 [!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/CPP/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]  
  
 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 演算法會並行運作。  因此，它不會按照預先決定的順序執行這些作業。  如果陣列包含此值的多個執行個體，結果可能就是任何一個位置。  
  
## 編譯程式碼  
 請複製範例程式碼並將它貼在 Visual Studio 專案中，或是貼在名為 `parallel-array-search.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc parallel\-array\-search.cpp**  
  
## 請參閱  
 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [平行演算法](../../parallel/concrt/parallel-algorithms.md)   
 [parallel\_for 函式](../Topic/parallel_for%20Function.md)   
 [cancellation\_token\_source 類別](../../parallel/concrt/reference/cancellation-token-source-class.md)