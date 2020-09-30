---
title: 從 OpenMP 移轉至並行執行階段
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, migrating from OpenMP
- OpenMP, migrating to the Concurrency Runtime
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
ms.openlocfilehash: 081d0ae8b312d827a0af98dd45c62f7563e81677
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507756"
---
# <a name="migrating-from-openmp-to-the-concurrency-runtime"></a>從 OpenMP 移轉至並行執行階段

並行執行階段支援多種不同的程式設計模型。 這些模型有可能相互重疊，但或許也可彌補其他程式庫之模型的不足之處。 本節中的檔比較 [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp) 與並行執行階段，並提供有關如何遷移現有的 OpenMP 程式碼以使用並行執行階段的範例。

OpenMP 程式設計模型是以開放標準定義的，具有定義完善的 Fortran 和 C/C++ 程式設計語言繫結。 Microsoft c + + 編譯器支援的 OpenMP 2.0 和2.5 版，非常適合反復使用的平行演算法;也就是說，它們會對資料陣列執行平行反覆運算。 OpenMP 3.0 除了反復的工作之外，還支援非反復作業。

當平行處理原則程度已預先決定且符合系統可用資源時，OpenMP 最有效率。 OpenMP 模型特別適用于高效能運算，其中極大的計算問題會分散到一部電腦的處理資源。 在此案例中，硬體環境通常是固定的，而且開發人員可以合理地預期在執行演算法時擁有所有計算資源的獨佔存取權。

不過，較不受限制的運算環境可能不符合 OpenMP 的建議。 例如， (的遞迴問題（例如快速排序演算法或搜尋) 資料的樹狀結構），使用 OpenMP 2.0 和2.5 可能更難執行。 並行執行階段藉由提供 [非同步代理](../../parallel/concrt/asynchronous-agents-library.md) 程式程式庫和 [平行模式程式庫](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) 來補充 OpenMP 的功能。 非同步代理程式程式庫支援粗略的工作平行處理;PPL 支援更精細的平行工作。 並行執行階段提供平行執行作業所需的基礎結構，讓您可以專注于應用程式的邏輯。 不過，由於並行執行階段可提供各種程式設計模型，因此其排程額外負荷可能會大於其他並行程式庫，例如 OpenMP。 因此，當您轉換現有的 OpenMP 程式碼以使用並行執行階段時，建議您以累加的方式測試效能。

## <a name="when-to-migrate-from-openmp-to-the-concurrency-runtime"></a>從 OpenMP 遷移至並行執行階段的時機

在下列情況下，將現有的 OpenMP 程式碼遷移為使用並行執行階段可能是很有利的。

|案例|並行執行階段的優點|
|-----------|-------------------------------------------|
|您需要可擴充的並行程式設計架構。|並行執行階段中有許多功能皆可進行擴充。 您也可以合併現有功能，以撰寫新功能。 因為 OpenMP 依賴編譯器指示詞，所以無法輕易擴充。|
|您的應用程式可受益于合作式封鎖。|當工作因為需要無法使用的資源而封鎖時，並行執行階段可以在第一項工作等候資源時執行其他工作。|
|您的應用程式可受益于動態負載平衡。|並行執行階段使用排程演算法，在工作負載變更時調整計算資源的配置。 在 OpenMP 中，當排程器將計算資源配置至平列區域時，系統會在整個計算期間修正這些資源配置。|
|您需要例外狀況處理支援。|PPL 可讓您攔截平列區域或迴圈內外的例外狀況。 在 OpenMP 中，您必須處理平列區域或迴圈內的例外狀況。|
|您需要取消機制。|PPL 可讓應用程式取消個別工作和平行的工作樹狀結構。 OpenMP 需要應用程式執行自己的取消機制。|
|您需要平行程式碼在其啟動的不同內容中完成。|並行執行階段可讓您在某個內容中啟動工作，然後在另一個內容中等待或取消該工作。 在 OpenMP 中，所有平行工作都必須在其啟動的內容中完成。|
|您需要增強的調試支援。|Visual Studio 提供 [ **平行堆疊** ] 和 [ **平行** 工作] 視窗，讓您可以更輕鬆地進行多執行緒應用程式的偵錯工具。<br /><br /> 如需有關並行執行階段的偵錯工具支援的詳細資訊，請參閱 [使用工作視窗](/visualstudio/debugger/using-the-tasks-window)、 [使用平行堆疊視窗](/visualstudio/debugger/using-the-parallel-stacks-window)和 [逐步解說：進行平行應用程式的偵錯工具](/visualstudio/debugger/walkthrough-debugging-a-parallel-application)。|

## <a name="when-not-to-migrate-from-openmp-to-the-concurrency-runtime"></a>不要從 OpenMP 遷移至並行執行階段

下列案例描述當您將現有的 OpenMP 程式碼遷移為使用並行執行階段時，可能不適合的時機。

|案例|說明|
|-----------|-----------------|
|您的應用程式已經符合您的需求。|如果您滿意應用程式效能和目前的偵錯工具支援，可能不適合進行遷移。|
|平行迴圈主體執行的工作很少。|並行執行階段工作排程器的額外負荷可能無法克服平行執行迴圈主體的優點，特別是當迴圈主體相對較小時時。|
|您的應用程式是以 C 撰寫。|由於並行執行階段使用許多 c + + 功能，因此當您無法撰寫可讓 C 應用程式完全使用的程式碼時，可能不適合使用。|

## <a name="related-topics"></a>[相關主題]

[如何：將 OpenMP parallel for 迴圈轉換成使用並行執行階段](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)

假設有一個使用 OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) 和 [for](../openmp/reference/openmp-directives.md#for-openmp) 指示詞的基本迴圈，示範如何將它轉換成使用並行執行階段 [Concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) 演算法。

[如何：轉換使用取消的 OpenMP 迴圈以使用並行執行階段](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)<br/>
針對不需要執行所有反覆運算的 OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp) 迴圈，示範如何將它轉換成使用並行執行階段取消機制。

[如何：轉換使用例外狀況處理的 OpenMP 迴圈以使用並行執行階段](../../parallel/concrt/convert-an-openmp-loop-that-uses-exception-handling.md)<br/>
針對執行例外狀況處理的 OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp) 迴圈，示範如何將它轉換成使用並行執行階段的例外狀況處理機制。

[如何：轉換使用縮減變數的 OpenMP 迴圈以使用並行執行階段](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)<br/>
針對使用[縮減](../openmp/reference/openmp-clauses.md#reduction)子句的 OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp)迴圈，示範如何將它轉換成使用並行執行階段。

## <a name="see-also"></a>另請參閱

[並行執行階段](../../parallel/concrt/concurrency-runtime.md)<br/>
[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)<br/>
[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)
