---
title: "平行模式程式庫 (PPL) | Microsoft Docs"
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
  - "平行模式程式庫 (PPL)"
ms.assetid: 40fd86b2-69fa-45e5-93d8-98a75636c242
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# 平行模式程式庫 (PPL)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

平行模式程式庫 (PPL) 提供命令式程式設計模型，可提升開發並存應用程式時的延展性和方便性。 PPL 建置在並行執行階段的排程和資源管理元件上。 其提供在資料上平行作用的泛型、類型安全演算法和容器，可提升應用程式程式碼與基礎執行緒機制之間的抽象層級。 PPL 有提供共用狀態的替代方案，也可以讓您開發可調整大小的應用程式。  
  
 PPL 提供下列功能：  
  
- *工作平行處理原則*︰ 一種機制，以平行方式執行數個工作項目 （工作） 的 Windows 執行緒集區上的運作方式  
  
- *平行演算法*︰ 泛型演算法，可做為並行執行階段上適用於平行的資料集合  
  
- *平行容器和物件*︰ 泛型容器類型，可讓您安全並行存取，其項目  
  
## <a name="example"></a>範例  
 PPL 提供類似標準範本庫 (STL) 的程式設計模型。 下列範例示範 PPL 的許多功能。 它會循序和平行計算數個 Fibonacci 數字。 這兩項計算都會 [array](../../standard-library/array-class-stl.md) 物件。 這個範例也會將執行這兩項計算所需的時間列印到主控台。  
  
 序列版會使用 STL [std:: for_each](../Topic/for_each.md) 演算法來周遊陣列，並將結果 [std:: vector](../../standard-library/vector-class.md) 物件。 平行版會執行相同的工作，但會使用 PPL [concurrency:: parallel_for_each](../Topic/parallel_for_each%20Function.md) 演算法，並將結果 [concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) 物件。 `concurrent_vector` 類別可讓每個迴圈反覆項目並行加入項目，而不需要同步處理對容器的寫入權限。  
  
 因為 `parallel_for_each` 會並行作用，所以此範例的平行版本必須將 `concurrent_vector` 物件排序，以產生與序列版相同的結果。  
  
 請注意，此範例使用 naïve 方法來計算 Fibonacci 數字；不過，這個方法會說明並行執行階段如何改善長時間運算的效能。  
  
 [!code-cpp[concrt-parallel-fibonacci#1](../../parallel/concrt/codesnippet/CPP/parallel-patterns-library-ppl_1.cpp)]  
  
 下列範例輸出適用於具有四個處理器的電腦。  
  
```Output  
serial time: 9250 ms  
parallel time: 5726 ms  
 
fib(24): 46368  
fib(26): 121393  
fib(41): 165580141  
fib(42): 267914296  
```  
  
 迴圈的每個反覆項目都需要不同的時間才能完成。 `parallel_for_each` 的效能受限於上次完成的作業。 因此，您不應預期此範例的序列版本與平行版本之間會有線性的效能改進。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|說明|  
|-----------|-----------------|  
|[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|說明 PPL 中工作和工作群組的角色。|  
|[平行演算法](../../parallel/concrt/parallel-algorithms.md)|說明如何使用平行演算法，例如 `parallel_for` 和 `parallel_for_each`。|  
|[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)|說明 PPL 提供的各種平行容器和物件。|  
|[取消](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation_in_the_ppl)|說明如何取消平行演算法正在執行的工作。|  
|[並行執行階段](../../parallel/concrt/concurrency-runtime.md)|說明並行執行階段，它可簡化平行程式設計，並包含相關主題的連結。|

