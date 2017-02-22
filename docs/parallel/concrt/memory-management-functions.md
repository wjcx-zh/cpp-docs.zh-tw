---
title: "記憶體管理函式 | Microsoft Docs"
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
  - "記憶體管理函式 [並行執行階段]"
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 記憶體管理函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件說明並行執行階段所提供、協助您以並行方式配置和釋放記憶體的記憶體管理函式。  
  
> [!TIP]
>  並行執行階段提供了預設排程器，因此您不需要在應用程式中建立排程器。  因為工作排程器有助於微調應用程式效能，如果您是並行執行階段的新使用者，建議請從[平行模式程式庫 \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md) 或[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)開始。  
  
 並行執行階段提供兩項經最佳化而能夠以並行方式配置和釋放記憶體區塊的記憶體管理函式。  [concurrency::Alloc](../Topic/Alloc%20Function.md) 函式可使用指定的大小配置記憶體區塊。  [concurrency::Free](../Topic/Free%20Function.md) 函式可釋放先前由 `Alloc` 配置的記憶體。  
  
> [!NOTE]
>  `Alloc` 和 `Free` 函式彼此相依。  `Free` 函式僅適用於釋放您以 `Alloc` 函式配置的記憶體。  此外，當您使用 `Alloc` 函式配置記憶體時，請使用 `Free` 函式釋放該記憶體。  
  
 當您配置和釋放不同執行緒或工作中一組固定的配置大小時，請使用 `Alloc` 和 `Free` 函式。  並行執行階段會從 C 執行階段堆積中快取它所配置的記憶體。  並行執行階段會為每個執行中的執行緒保留一個獨立的記憶體快取；因此，執行階段在管理記憶體時無須使用鎖定或記憶體屏障。  記憶體快取的存取頻率愈高，`Alloc` 和 `Free` 函式對應用程式的效用就愈明顯。  例如，經常同時呼叫 `Alloc` 和 `Free` 的執行緒相較於主要僅呼叫 `Alloc` 或 `Free` 的執行緒，前者的受益程度較高。  
  
> [!NOTE]
>  當您使用這些記憶體管理函式時，如果您的應用程式使用大量記憶體，應用程式可能會比預期更快進入記憶體不足的情況。  由於一個執行緒所快取的記憶體區塊無法供其他任何執行緒使用，因此當某個執行緒佔用大量記憶體時，該記憶體即無法另作他用。  
  
## 範例  
 如需使用 `Alloc` 和 `Free` 函式改善記憶體效能的範例，請參閱 [如何：使用 Alloc 和 Free 改善記憶體效能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)。  
  
## 請參閱  
 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [如何：使用 Alloc 和 Free 改善記憶體效能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)