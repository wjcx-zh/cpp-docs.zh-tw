---
title: 工作排程器 （並行執行階段） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- oversubscription [Concurrency Runtime]
- task scheduler [Concurrency Runtime], oversubscription
- schedule groups [Concurrency Runtime]
- task scheduler [Concurrency Runtime], lightweight tasks
- task scheduler [Concurrency Runtime]
- lightweight tasks [Concurrency Runtime]
- task scheduler [Concurrency Runtime], scheduler policies
- task scheduler [Concurrency Runtime], schedule groups
- wait function [Concurrency Runtime]
- task scheduler [Concurrency Runtime], scheduler instances
- scheduler instances [Concurrency Runtime]
- scheduler policies [Concurrency Runtime]
- task scheduler [Concurrency Runtime], wait function
ms.assetid: 9aba278c-e0c9-4ede-b7c6-fedf7a365d90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b76aaa0310e9f481ea65a0ab0600a0e3ae6aed7c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="task-scheduler-concurrency-runtime"></a>工作排程器 (並行執行階段)
文件中這一部分的主題將說明並行執行階段工作排程器的重要功能。 工作排程器適用於您想要微調使用並行執行階段之現有程式碼的效能時。  
  
> [!IMPORTANT]
>  無法從通用 Windows 平台 (UWP) 應用程式使用工作排程器。 如需詳細資訊，請參閱[建立非同步作業以 c + + UWP 應用程式](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)。  
>   
>  在 Visual Studio 2015 和更新版本， [concurrency:: task](../../parallel/concrt/reference/task-class.md)類別及 ppltasks.h 中的相關的類型使用 Windows 執行緒集區做為其排程器。 本主題不再適用於 ppltasks.h 中所定義的類型。 平行演算法 (例如 parallel_for) 會繼續使用並行執行階段做為預設排程器。  
  
> [!TIP]
>  並行執行階段會提供預設排程器，因此您不需要在應用程式中建立排程器。 由於工作排程器可協助您微調應用程式的效能，我們建議您開始[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)如果您是新的並行執行階段。  
  
 工作排程器會在執行階段排定並協調工作。 A*工作*是執行特定工作的工作單位。 工作通常可以與其他工作平行執行。 工作群組項目、平行演算法和非同步代理程式所執行的工作都是工作的範例。  
  
 工作排程器會管理與在具有多個運算資源的電腦上有效率地排定工作相關的詳細資料。 工作排程器也會使用基礎作業系統的最新功能。 因此，使用並行執行階段的應用程式會在具有擴充功能的硬體上自動調整及改善。  
  
 [與其他並行模型的比較](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)描述先佔式與合作式排程機制之間的差異。 工作排程器使用合作式排程及工作竊取演算法，搭配作業系統的先佔式排程器，來達到處理資源的最大使用率。  
  
 並行執行階段提供預設排程器，讓您不需要管理基礎結構的細節。 因此，您通常不會直接使用工作排程器。 不過，為了滿足應用程式的品質需求，您可以使用工作排程器，提供自己的排程原則或建立排程器與特定工作的關聯。 例如，假設您有無法擴充超過四個處理器的平行排序常式， 您可以使用*排程器原則*建立會產生四個以上的並行工作排程器。 在這個排程器上執行排序常式可讓其他作用中排程器使用任何剩餘的處理資源。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[排程器執行個體](../../parallel/concrt/scheduler-instances.md)|描述排程器執行個體，以及如何使用 `concurrency::Scheduler` 和 `concurrency::CurrentScheduler` 類別加以管理。 當您想要建立明確排程原則與特定類型工作負載的關聯時，請使用排程器執行個體。|  
|[排程器原則](../../parallel/concrt/scheduler-policies.md)|描述排程器原則的角色。 當您想要控制排程器在管理工作時使用的策略，請使用排程器原則。|  
|[排程群組](../../parallel/concrt/schedule-groups.md)|描述排程群組的角色。 當您需要在工作之間有高度位置關係時 (例如一個相關工作的群組可因為在相同處理器節點上執行而受益)，請使用排程群組。|  
|[輕量型工作](../../parallel/concrt/lightweight-tasks.md)|描述輕量型工作的角色。 輕量型工作適用於當您調整現有程式碼以使用並行執行階段的排程功能時。|  
|[內容](../../parallel/concrt/contexts.md)|描述內容的角色、`concurrency::wait` 函式，和 `concurrency::Context` 類別。 當您需要控制內容封鎖、解除封鎖及產生等時機，或想要啟用應用程式中的過度訂閱時，請使用這項功能。|  
|[記憶體管理函式](../../parallel/concrt/memory-management-functions.md)|描述 `concurrency::Alloc` 和 `concurrency::Free` 函式。 這些函式可以藉由以並行方式配置和釋放記憶體，來改善記憶體效能。|  
|[與其他並行模型的比較](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|描述先佔式與合作式排程機制之間的差異。|  
|[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|描述如何在您的應用程式中使用不同的平行模式，例如平行演算法。|  
|[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)|描述如何在您的應用程式中使用非同步代理程式。|  
|[並行執行階段](../../parallel/concrt/concurrency-runtime.md)|說明並行執行階段，它可簡化平行程式設計，並包含相關主題的連結。|

