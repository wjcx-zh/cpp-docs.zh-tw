---
title: "如何：使用 Alloc 和 Free 改善記憶體效能 | Microsoft Docs"
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
  - "Alloc 和 Free，使用 [並行執行階段]"
  - "使用 Alloc 和 Free [並行執行階段]"
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 Alloc 和 Free 改善記憶體效能
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件將示範如何使用 [concurrency::Alloc](../Topic/Alloc%20Function.md) 和 [concurrency::Free](../Topic/Free%20Function.md) 函式來改善記憶體效能。  它會針對三個指定 `new` 和 `delete` 運算子的不同型別，比較以平行方式反轉陣列元素所需的時間。  
  
 當多個執行緒經常同時呼叫 `Alloc` 和 `Free` 時，`Alloc` 和 `Free` 函式最有用。  執行階段會為每個執行緒保留一個獨立的記憶體快取；因此，執行階段在管理記憶體時無須使用鎖定或記憶體屏障。  
  
## 範例  
 下列範例顯示三個指定 `new` 和 `delete` 運算子的型別。  `new_delete` 類別會使用全域 `new` 和 `delete` 運算子、`malloc_free` 類別會使用 C 執行階段 [malloc](../../c-runtime-library/reference/malloc.md) 和 [free](../../c-runtime-library/reference/free.md) 函式，而 `Alloc_Free` 類別會使用並行執行階段 `Alloc` 和 `Free` 函式。  
  
 [!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/CPP/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]  
  
## 範例  
 下列範例顯示 `swap` 和 `reverse_array` 函式。  `swap` 函式會交換位於指定之索引處的陣列內容。  它會針對暫存變數配置堆積中的記憶體。  `reverse_array` 函式會建立大型陣列並且比較以平行方式反轉該陣列許多次所需的時間。  
  
 [!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/CPP/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]  
  
## 範例  
 下列範例顯示 `wmain` 函式，此函式會計算針對 `new_delete`、`malloc_free` 和 `Alloc_Free` 型別 \(每個型別都使用不同的記憶體配置\) 執行 `reverse_array` 函式所需的時間。  
  
 [!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/CPP/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]  
  
## 範例  
 完整的程式碼範例如下所示。  
  
 [!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/CPP/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]  
  
 這個範例會在配備四個處理器的電腦上產生下列範例輸出。  
  
  **new 花費 2031 毫秒\/刪除。**  
**malloc 花費 1672 毫秒 \/釋放 。**  
**採用了 Alloc\/可用的 656 毫秒。** 在這個範例中，使用 `Alloc` 和 `Free` 函式的型別會提供最佳的記憶體效能，因為 `Alloc` 和 `Free` 函式已針對多個執行緒中經常配置和釋放的記憶體區塊最佳化。  
  
## 編譯程式碼  
 請複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼在名為 `allocators.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc allocators.cpp**  
  
## 請參閱  
 [記憶體管理函式](../../parallel/concrt/memory-management-functions.md)   
 [Alloc 函式](../Topic/Alloc%20Function.md)   
 [Free 函式](../Topic/Free%20Function.md)