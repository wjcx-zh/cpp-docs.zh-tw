---
title: "比較並行執行階段與其他並行模型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Concurrency Runtime, compared to other models
ms.assetid: d8b9a1f4-f15f-43c3-a5b4-c0991edf9c86
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e20523eb8a2c78cfa72b6c3084e9ca9f620a916c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="comparing-the-concurrency-runtime-to-other-concurrency-models"></a>比較並行執行階段和其他並行模型
本文件說明並行執行階段和其他技術在功能和程式設計模型方面的差異。 藉由了解並行執行階段優點與其他程式設計模型優點的比較結果，您可以選取最符合應用程式需求的技術。  
  
 如果您目前使用 Windows 執行緒集區或 OpenMP 等其他程式設計模型，在某些情況下適合移轉至並行執行階段。 例如， [Migrating from OpenMP to the Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md) 主題說明何時適合從 OpenMP 移轉至並行執行階段。 不過，如果您對應用程式效能和目前的偵錯支援感到滿意，則不需要移轉。  
  
 您可以利用並行執行階段的功能和生產力優勢，彌補使用其他並行模型之現有應用程式的不足之處。 當多個工作排程器爭用相同運算資源時，並行執行階段無法保證負載平衡。 不過，當工作負載不重疊時，此影響幾乎不存在。  
  
##  <a name="top"></a> 章節  
  
-   [比較先佔式排程與合作式排程](#models)  
  
-   [比較並行執行階段與 Windows API](#winapi)  
  
-   [比較並行執行階段與 OpenMP](#openmp)  
  
##  <a name="models"></a> 比較先佔式排程與合作式排程  
 先佔式模型與合作式排程模型是兩種可讓多項工作共用運算資源 (例如處理器或硬體執行緒) 的常用方式。  
  
### <a name="preemptive-and-cooperative-scheduling"></a>先佔式與合作式排程  
 *「先佔式排程」* (preemptive scheduling) 是具有優先順序的循環配置資源機制，可在指定的期間內將運算資源的獨佔存取權指定給每項工作，然後再切換到另一項工作。 先佔式排程是多工作業系統 (例如 Windows) 中的常用方式。「合作式排程」(Cooperative scheduling) 機制可讓每項工作獨佔存取運算資源，直到工作完成或工作讓渡其資源存取權為止。 並行執行階段可使用合作式排程搭配作業系統的先佔式排程器，來達成處理資源的最大使用量。  
  
### <a name="differences-between-preemptive-and-cooperative-schedulers"></a>先佔式排程器與合作式排程器之間的差異  
 先佔式排程器會設法讓多個執行緒獲得相同的運算資源存取權，以確保每個執行緒都能順利執行作業。 在運算資源充足的電腦上不難確保平均存取；但要確保有效率的資源使用，則仍有一定的難度。  
  
 使用先佔式核心模式排程器時，應用程式程式碼必須依賴作業系統來制定排程決策。 相反地，使用者模式合作式排程器可讓應用程式程式碼自行制定其排程決策。 合作式排程可讓應用程式制定許多排程決策，因而能夠大幅降低與核心模式同步處理相關聯的額外負荷。 當合作式排程器沒有其他要排程的工作時，通常會將排程決策交由作業系統核心處理。 如果有封鎖作業傳送至核心，但該作業並未傳送至使用者模式排程器，則合作式排程器也會將決策交由作業系統排程器處理。  
  
### <a name="cooperative-scheduling-and-efficiency"></a>合作式排程與效率  
 對先佔式排程器而言，所有具有相同優先順序層級的工作都是相等的。 先佔式排程器通常會依照執行緒的建立順序來排程執行緒。 此外，先佔式排程器會以循環配置資源的方式，根據執行緒優先順序為每個執行緒指定時間配量。 雖然這項機制提供了公平性 (每個執行緒都會順利進行)，但效率卻會有一定程度的減損。 例如，有許多計算密集型演算法並不需要公平性。 相反地，它所著重的是相關工作必須在最短的整體時間內完成。 合作式排程可讓應用程式更有效率地排程工作。 例如，假設某個應用程式有許多執行緒。 將未共用資源的執行緒排程為並行執行，可降低同步處理額外負荷，進而提升效率。 另一種有效排程工作的方式，是在相同的處理器上執行工作的管線 (其中每項工作都會以前一項工作的輸出為基礎而執行)，讓每個管線階段的輸入事先載入到記憶體快取中。  
  
### <a name="using-preemptive-and-cooperative-scheduling-together"></a>同時使用先佔式排程與合作式排程  
 合作式排程無法解決所有的排程問題。 例如，未平均讓渡給其他工作的工作，可能會耗用所有的可用運算資源，而使其他工作無法執行。 並行執行階段利用合作式排程的效率優勢，彌補先佔式排程必須確保公平性的不足之處。 根據預設，並行執行階段會提供使用工作竊取演算法的合作式排程器，有效地將工作分配給運算資源。 不過，並行執行階段排程器也依賴作業系統的先佔式排程器，以公平地在應用程式之間分配資源。 您也可以在應用程式中建立自訂排程器和排程器原則，以便精密地控制執行緒執行。  
  
 [[靠上](#top)]  
  
##  <a name="winapi"></a> 比較並行執行階段與 Windows API  
 Microsoft Windows 應用程式開發介面 (通常稱為 Windows API，其前身為 Win32) 提供可讓應用程式並行處理的程式設計模型。 並行執行階段建置於 Windows API 上，可另行提供無法從基礎作業系統使用的其他程式設計模型。  
  
 並行執行階段建置於 Windows API 執行緒模型上，用以執行平行工作。 它也會使用 Windows API 記憶體管理和執行緒區域儲存區機制。 在 Windows 7 和 Windows Server 2008 R2 上，它會以 Windows API 支援使用者可排程的執行緒，以及硬體執行緒超過 64 個的電腦。 並行執行階段可提供合作式工作排程器和工作竊取演算法，讓運算資源發揮最大的效用，並且可讓多個排程器執行個體同時運作，以擴充 Windows API 模型。  
   
### <a name="programming-languages"></a>程式語言：  
 Windows API 可使用 C 程式設計語言公開程式設計模型。 並行執行階段提供可利用 C++ 語言之最新功能的 C++ 程式設計介面。 例如，Lambda 函式可提供型別安全的簡潔機制，用以定義平行工作函式。 如需並行執行階段所使用之最新 C++ 功能的詳細資訊，請參閱[概觀](../../parallel/concrt/asynchronous-message-blocks.md)。  
  
### <a name="threads-and-thread-pools"></a>執行緒與執行緒集區  
 Windows API 的中央並行機制是執行緒。 您通常會使用 [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) 函式來建立執行緒。 雖然執行緒相對而言較易建立及使用，但是作業系統必須配置大量的時間與其他資源來管理執行緒。 此外，雖然能確保每個執行緒的執行時間與相同優先順序層級上的任何其他執行緒相同，但您必須建立夠大型工作，才能因應相關聯的額外負荷。 針對較小或較精細的工作，與並行相關聯的額外負荷，可能會高於以平行方式執行工作的優點。  
  
 執行緒集區是能夠減少執行緒管理成本的方式之一。 自訂執行緒集區以及 Windows API 所提供的執行緒集區實作，都能夠讓小型工作項目有效地以平行方式執行。 Windows 執行緒集區將工作項目保存在先進先出 (FIFO) 佇列中。 每個工作項目都會以其加入集區的順序啟動。  
  
 並行執行階段實作工作竊取演算法，來擴充 FIFO 排程機制。 此演算法會將尚未啟動的工作，移至工作項目用盡的執行緒。 雖然工作竊取演算法可以平衡工作負載，但也可能會導致工作項目重新排序。 此重新排序程序可能會導致工作項目以不同於提交的順序啟動。 這對遞迴演算法會很有用，在這些演算法中的資料較有可能在新工作之間共用，而不是在舊工作之間共用。 讓新項目先執行，意味著快取遺失甚或分頁錯誤的情況都會減少。  
  
 從作業系統的觀點來看，工作竊取是不公平的。 但在應用程式實作要以平行方式執行的演算法或工作時，子工作之間公平性有時並不重要。 重要的是整體工作的完成速度。 對其他演算法而言，FIFO 也是適當的排程策略。  
  
### <a name="behavior-on-various-operating-systems"></a>各種作業系統上的行為  
 在 Windows XP 和 Windows Vista 上，使用並行執行階段的應用程式行為大致相同，不同之處在於 Windows Vista 的堆積效能已有所改善。  
  
 在 Windows 7 和 Windows Server 2008 R2 中，作業系統可進一步支援並行和延展性。 例如，這些作業系統可支援硬體執行緒超過 64 個的電腦。 使用 Windows API 的現有應用程式必須經過修改，才能利用這些新功能。 不過，使用並行執行階段的應用程式則會自動使用這些功能，而不需要修改。  
  
 [base.user-mode_scheduling](http://msdn.microsoft.com/library/windows/desktop/dd627187)  
  
 [[靠上](#top)]  
  
##  <a name="openmp"></a> 比較並行執行階段與 OpenMP  
 並行執行階段支援多種不同的程式設計模型。 這些模型有可能相互重疊，但或許也可彌補其他程式庫之模型的不足之處。 本節將比較並行執行階段與 [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)。  
  
 OpenMP 程式設計模型是以開放標準定義的，具有定義完善的 Fortran 和 C/C++ 程式設計語言繫結。 OpenMP 2.0 和 2.5 版均適用於反覆執行的平行演算法；也就是說，它們可對資料陣列執行平行的反覆運算。 當平行處理原則程度已預先決定且符合系統可用資源時，OpenMP 最有效率。 OpenMP 模型特別適用於高效能運算，因為在此環境中，非常龐大的計算問題會分散到一部電腦的不同處理資源。 在此情況下，硬體環境為已知，因此開發人員可以在執行演算法時，合理預期能夠取得運算資源的獨佔存取權。  
  
 不過，在其他較不受限制的運算環境中，OpenMP 可能不適用。 例如，使用 OpenMP 時，較不易實作遞迴問題 (例如快速排序演算法或搜尋資料的樹狀結構)。 並行執行階段提供了 [平行模式程式庫](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) 和 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)，可彌補 OpenMP 功能的不足之處。 不同於 OpenMP，並行執行階段所提供的動態排程器可根據可用資源進行調整，並且可隨著工作負載的變更而調整平行處理原則的程度。  
  
 並行執行階段中有許多功能皆可進行擴充。 您也可以合併現有功能，以撰寫新功能。 由於 OpenMP 依賴編譯器指示詞，因此不易擴充。  
  
 如需並行執行階段與 OpenMP 的比較，以及如何移轉現有的 OpenMP 程式碼以使用並行執行階段的詳細資訊，請參閱 [Migrating from OpenMP to the Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)。  
  
 [[靠上](#top)]  
  
## <a name="see-also"></a>請參閱  
 [並行執行階段](../../parallel/concrt/concurrency-runtime.md)     
 [概觀](../../parallel/concrt/asynchronous-message-blocks.md)   
 [平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)
