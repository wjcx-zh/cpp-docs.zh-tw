---
title: 記憶體管理函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory management functions [Concurrency Runtime]
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0a298c7fb9e50bb17d37224b69ce342c54115d7
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="memory-management-functions"></a>記憶體管理函式
本文件說明並行執行階段提供可協助您配置和釋放記憶體以並行方式記憶體管理函式。  
  
> [!TIP]
>  並行執行階段會提供預設排程器，因此您不需要在應用程式中建立排程器。 由於工作排程器可協助您微調應用程式的效能，我們建議您開始[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)如果您是新的並行執行階段。  
  
 並行執行階段提供兩種記憶體管理函式，配置和釋放記憶體區塊，以並行方式最佳化。 [Concurrency:: alloc](reference/concurrency-namespace-functions.md#alloc)函式會使用指定的大小配置記憶體區塊。 [Concurrency:: free](reference/concurrency-namespace-functions.md#free)函式會釋放已配置的記憶體`Alloc`。  
  
> [!NOTE]
>  `Alloc`和`Free`函式都必須。 使用`Free`函式只可使用所配置的記憶體釋放`Alloc`函式。 此外，當您使用`Alloc`函式配置的記憶體，請只使用`Free`函式，以釋放記憶體。  
  
 使用`Alloc`和`Free`函式，當您配置和釋放一組固定的配置大小，從不同執行緒或工作。 並行執行階段會快取它從 C 執行階段堆積中配置的記憶體。 並行執行階段會保存不同的記憶體快取的每個執行中的執行緒。因此，runtime 負責管理記憶體，而不使用鎖定或記憶體屏障。 應用程式有益於多個從`Alloc`和`Free`函式更頻繁地存取記憶體快取時。 例如，經常會同時呼叫執行緒`Alloc`和`Free`主要呼叫執行緒以外的更多的優點`Alloc`或`Free`。  
  
> [!NOTE]
>  當您使用這些記憶體管理函式，而且可能需要輸入您的應用程式使用大量記憶體，應用程式記憶體不足的狀況更快地比您預期。 因為一個執行緒不會快取的記憶體區塊不能使用任何其他的執行緒，如果一個執行緒保存大量的記憶體，所以無法使用記憶體。  
  
## <a name="example"></a>範例  
 如需範例，會使用`Alloc`和`Free`函式來改善記憶體效能，請參閱[How to： 使用 Alloc 和 Free 改善記憶體效能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)。  
  
## <a name="see-also"></a>另請參閱  
 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [如何：使用 Alloc 和 Free 改善記憶體效能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)

