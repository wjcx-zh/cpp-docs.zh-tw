---
title: 平行模式程式庫 (PPL) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Parallel Patterns Library (PPL)
ms.assetid: 40fd86b2-69fa-45e5-93d8-98a75636c242
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7263d764014fa3532c3234bd4c7a0d4f1ff8d3c3
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691537"
---
# <a name="parallel-patterns-library-ppl"></a>平行模式程式庫 (PPL)
平行模式程式庫 (PPL) 提供命令式程式設計模型，可提升開發並存應用程式時的延展性和方便性。 PPL 建置在並行執行階段的排程和資源管理元件上。 其提供在資料上平行作用的泛型、類型安全演算法和容器，可提升應用程式程式碼與基礎執行緒機制之間的抽象層級。 PPL 有提供共用狀態的替代方案，也可以讓您開發可調整大小的應用程式。  
  
 PPL 提供下列功能：  
  
- *工作平行處理原則*： 一種機制可在 Windows 執行緒集區平行執行數個工作項目 （工作） 上運作，  
  
- *平行演算法*： 做為並行執行階段可運作以平行的資料集合的泛型演算法  
  
- *平行容器和物件*： 泛型容器類型，可提供安全並行存取其項目  
  
## <a name="example"></a>範例  
 PPL 提供類似於 c + + 標準程式庫的程式設計模型。 下列範例示範 PPL 的許多功能。 它會循序和平行計算數個 Fibonacci 數字。 這兩項計算處理[std:: array](../../standard-library/array-class-stl.md)物件。 這個範例也會將執行這兩項計算所需的時間列印到主控台。  
  
 序列版會使用 c + + 標準程式庫[std:: for_each](../../standard-library/algorithm-functions.md#for_each)演算法來周遊陣列，並將結果[std:: vector](../../standard-library/vector-class.md)物件。 平行版會執行相同的工作，但會使用 PPL [concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)演算法，並將結果[concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)物件。 `concurrent_vector` 類別可讓每個迴圈反覆項目並行加入項目，而不需要同步處理對容器的寫入權限。  
  
 因為 `parallel_for_each` 會並行作用，所以此範例的平行版本必須將 `concurrent_vector` 物件排序，以產生與序列版相同的結果。  
  
 請注意，此範例使用 naïve 方法來計算 Fibonacci 數字；不過，這個方法會說明並行執行階段如何改善長時間運算的效能。  
  
 [!code-cpp[concrt-parallel-fibonacci#1](../../parallel/concrt/codesnippet/cpp/parallel-patterns-library-ppl_1.cpp)]  
  
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
  
|標題|描述|  
|-----------|-----------------|  
|[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|說明 PPL 中工作和工作群組的角色。|  
|[平行演算法](../../parallel/concrt/parallel-algorithms.md)|說明如何使用平行演算法，例如 `parallel_for` 和 `parallel_for_each`。|  
|[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)|說明 PPL 提供的各種平行容器和物件。|  
|[PPL 中的取消](cancellation-in-the-ppl.md)|說明如何取消平行演算法正在執行的工作。|  
|[並行執行階段](../../parallel/concrt/concurrency-runtime.md)|說明並行執行階段，它可簡化平行程式設計，並包含相關主題的連結。|

