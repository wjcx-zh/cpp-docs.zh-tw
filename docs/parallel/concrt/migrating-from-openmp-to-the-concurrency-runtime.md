---
title: "從 OpenMP 移轉至並行執行階段 | Microsoft Docs"
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
  - "並行執行階段, 從 OpenMP 移轉"
  - "OpenMP, 移轉至並行執行階段"
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
caps.latest.revision: 12
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 從 OpenMP 移轉至並行執行階段
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

並行執行階段支援多種不同的程式設計模型。  這些模型有可能相互重疊，但或許也可彌補其他程式庫的模型之不足。  本節的文件比較 [OpenMP](../../parallel/openmp/openmp-in-visual-cpp.md) 與並行執行階段，並提供如何移轉現有 OpenMP 程式碼以使用並行執行階段的範例。  
  
 OpenMP 程式設計模型是以開放標準定義的，具有定義完善的 Fortran 和 C\/C\+\+ 程式設計語言繫結。  OpenMP 2.0 和 2.5 版 \(受 Visual C\+\+ 編譯器支援\) 均適用於反覆執行的平行演算法；也就是說，它們可對資料陣列執行平行的反覆運算。  除了反覆執行的工作之外，OpenMP 3.0 還支援非反覆執行的工作。  
  
 當平行處理原則程度已預先決定且符合系統可用資源時，OpenMP 最有效率。  OpenMP 模型特別適用於高效能運算，因為在此環境中非常龐大的計算問題會分散到一部電腦的處理資源。  在這種情況下，硬體環境通常是固定的，開發人員可在演算法執行時按理預期能夠取得所有運算資源的獨佔存取權。  
  
 但在較不受限制的運算環境中，則可能不適用使用 OpenMP。  例如，在使用 OpenMP 2.0 和 2.5 時較不易實作遞迴問題 \(例如快速排序演算法或搜尋資料的樹狀結構\)。  並行執行階段提供了[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)和[平行模式程式庫](../../parallel/concrt/parallel-patterns-library-ppl.md) \(PPL\)，藉以彌補 OpenMP 功能的不足之處。  非同步代理程式程式庫支援粗略工作的平行處理原則，而 PPL 則支援較精細的平行工作。  並行執行階段提供了平行執行作業所需的基礎結構，讓您可以專注於應用程式的邏輯。  不過，因為並行執行階段啟用各種程式撰寫模型，它的排程額外負荷可能大於其他並行程式庫 \(例如 OpenMP\)。  因此，建議您在轉換現有的 OpenMP 程式碼以使用並行執行階段時，累加測試效能。  
  
## 從 OpenMP 移轉至並行執行階段的時機  
 在下列案例中，移轉現有 OpenMP 程式碼以使用並行執行階段，可能很有用處。  
  
|案例|並行執行階段的好處|  
|--------|---------------|  
|您需要可延伸的並行程式設計架構。|並行執行階段中有許多功能皆可進行擴充。  您也可以合併現有功能，以撰寫新功能。  由於 OpenMP 依賴編譯器指示詞，因此不易擴充。|  
|您的應用程式要從合作式封鎖中獲益。|當工作因為所需資源尚不可得而封鎖時，並行執行階段可以在第一個工作等候資源的同時，執行其他工作。|  
|您的應用程式要從動態負載平衡中獲益。|並行執行階段會使用排程演算法，這個排程演算法會隨著工作負載變更而調整運算資源配置。  在 OpenMP 中，當排程器將運算資源配置給平行區域時，這些資源配置在整個運算過程中都是固定的。|  
|您需要例外狀況處理支援。|PPL 讓您可在平行區域或迴圈內部和外部攔截例外狀況。  在 OpenMP 中，您必須在平行區域或迴圈內部處理例外狀況。|  
|您需要取消機制。|PPL 可讓應用程式取消個別工作和平行工作樹狀結構。  OpenMP 需要應用程式實作自己的取消機制。|  
|您需要平行程式碼在不同於最初開始的內容中完成。|並行執行階段可讓您在某個內容中啟動工作，然後在另一個內容中等候或取消該工作。  在 OpenMP 中，所有平行工作都必須在最初開始的內容中完成。|  
|您需要增強偵錯支援。|Visual Studio 提供了 \[**平行堆疊**\] 和 \[**平行工作**\] 視窗，讓您可以更輕鬆地偵錯多執行緒應用程式。<br /><br /> 如需並行執行階段偵錯支援的詳細資料，請參閱[使用工作視窗](../Topic/Using%20the%20Tasks%20Window.md)、[使用平行堆疊視窗](../Topic/Using%20the%20Parallel%20Stacks%20Window.md)和[逐步解說：偵錯平行應用程式](../Topic/Walkthrough:%20Debugging%20a%20Parallel%20Application.md)。|  
  
## 不從 OpenMP 移轉至並行執行階段的時機  
 下列案例說明不適合移轉現有 OpenMP 程式碼以使用並行執行階段的時機。  
  
|案例|說明|  
|--------|--------|  
|您的應用程式已符合需求。|如果您對應用程式效能和目前的偵錯支援感到滿意，移轉可能不適合。|  
|您的平行迴圈主體執行少量工作。|並行執行階段工作排程器的額外負荷可能大於平行執行迴圈主體的好處，特別是在迴圈主體相當小時。|  
|您的應用程式以 C 撰寫。|因為並行執行階段使用許多 C\+\+ 功能，當您無法撰寫可讓 C 應用程式完全利用它的程式碼時，可能不適合。|  
  
## 相關主題  
 [如何：轉換 OpenMP parallel for 迴圈來使用並行執行階段](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)  
 指定使用 OpenMP [parallel](../../parallel/openmp/reference/parallel.md) 和 [for](../../parallel/openmp/reference/for-openmp.md) 指示詞的基本迴圈，示範如何將它轉換為使用並行執行階段 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 演算法。  
  
 [如何：轉換使用取消的 OpenMP 迴圈來使用並行執行階段](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)  
 指定不需要所有反覆項目執行的 OpenMP [parallel](../../parallel/openmp/reference/parallel.md) [for](../../parallel/openmp/reference/for-openmp.md) 迴圈，示範如何將它轉換為使用並行執行階段取消機制。  
  
 [如何：轉換使用例外狀況處理的 OpenMP 迴圈來使用並行執行階段](../../parallel/concrt/convert-an-openmp-loop-that uses-exception-handling.md)  
 指定可執行例外狀況處理的 OpenMP [parallel](../../parallel/openmp/reference/parallel.md) [for](../../parallel/openmp/reference/for-openmp.md) 迴圈，示範如何將它轉換為使用並行執行階段例外狀況處理機制。  
  
 [如何：轉換使用削減變數的 OpenMP 迴圈來使用並行執行階段](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)  
 指定可使用 [reduction](../../parallel/openmp/reference/reduction.md) 子句的 OpenMP [parallel](../../parallel/openmp/reference/parallel.md) [for](../../parallel/openmp/reference/for-openmp.md) 迴圈，示範如何將它轉換為使用並行執行階段。  
  
## 請參閱  
 [並行執行階段](../../parallel/concrt/concurrency-runtime.md)   
 [OpenMP](../../parallel/openmp/openmp-in-visual-cpp.md)   
 [平行模式程式庫 \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)