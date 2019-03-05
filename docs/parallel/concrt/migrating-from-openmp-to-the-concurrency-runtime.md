---
title: 從 OpenMP 移轉至並行執行階段
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, migrating from OpenMP
- OpenMP, migrating to the Concurrency Runtime
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
ms.openlocfilehash: 16b0f175867e18e127997749098cce998674b3d2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259499"
---
# <a name="migrating-from-openmp-to-the-concurrency-runtime"></a>從 OpenMP 移轉至並行執行階段

並行執行階段支援多種不同的程式設計模型。 這些模型有可能相互重疊，但或許也可彌補其他程式庫之模型的不足之處。 在此文件一節比較[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)為並行執行階段，並提供有關如何移轉現有的 OpenMP 程式碼，以使用並行執行階段的範例。

OpenMP 程式設計模型是以開放標準定義的，具有定義完善的 Fortran 和 C/C++ 程式設計語言繫結。 OpenMP 版本 2.0 和 2.5 支援的 Visual c + + 編譯器，非常適合平行演算法反覆;也就是它們會透過資料的陣列執行平行的反覆項目。 OpenMP 3.0 支援非反覆執行的工作，除了反覆執行的工作。

當平行處理原則程度已預先決定且符合系統可用資源時，OpenMP 最有效率。 OpenMP 模型特別適的符合高效能運算，非常龐大的計算問題會分散到一部電腦的處理資源的位置。 在此案例中，硬體環境通常固定的開發人員可以合理預期能夠取得所有的運算資源的獨佔存取權，當執行演算法。

不過，比較不受條件約束的運算環境可能不完全相符的 OpenMP。 例如，遞迴問題 （例如快速排序演算法或搜尋樹狀結構的資料） 會比較難實作使用 OpenMP 2.0 和 2.5。 並行執行階段藉由提供補充功能的 OpenMP [Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)並[平行模式程式庫](../../parallel/concrt/parallel-patterns-library-ppl.md)(PPL)。 非同步代理程式程式庫支援廣泛的工作平行處理原則;PPL 支援更多更細緻的平行工作。 並行執行階段提供的基礎結構，才能以平行方式執行作業，以便您專注於您的應用程式的邏輯。 不過，由於並行執行階段可讓各種不同的程式設計模型，其排程額外負荷可能大於其他的並行處理程式庫，例如 OpenMP。 因此，我們建議您先以累加方式測試效能時轉換您現有的 OpenMP 程式碼，以使用並行執行階段。

## <a name="when-to-migrate-from-openmp-to-the-concurrency-runtime"></a>從 OpenMP 移轉至並行執行階段的時機

它可能較有利移轉現有的 OpenMP 程式碼，以在下列情況中使用並行執行階段。

|Cases|並行執行階段的優點|
|-----------|-------------------------------------------|
|您需要的可延伸的並行程式設計架構。|並行執行階段中有許多功能皆可進行擴充。 您也可以合併現有功能，以撰寫新功能。 由於 OpenMP 依賴編譯器指示詞，它無法輕鬆地擴充。|
|您的應用程式能否獲益合作式封鎖。|當工作阻擋，因為它需要尚無法使用的資源時，並行執行階段可以在第一項工作等候資源時執行其他工作。|
|您的應用程式會受益於動態負載平衡。|並行執行階段會使用調整運算資源，隨著工作負載變更配置排程演算法。 在 OpenMP，當排程器配置運算資源可在平行區域，這些資源配置被固定整個計算。|
|您需要例外狀況處理支援。|PPL 可讓您攔截例外狀況的內部和外部的平行區域或迴圈。 在 OpenMP，您必須處理迴圈的平行區域內的例外狀況。|
|您需要取消機制。|PPL 讓取消個別工作和平行工作樹狀結構的應用程式。 OpenMP 需要應用程式實作自己的取消機制。|
|您需要完成啟動所在的不同內容中的平行程式碼。|並行執行階段可讓您在某個內容中，啟動工作，然後等候或取消該工作在其他內容中。 OpenMP，在所有的平行工作必須完成啟動所在的內容中。|
|您需要增強的偵錯支援。|Visual Studio 提供**平行堆疊**並**平行工作**windows，讓您更輕鬆地偵錯多執行緒應用程式。<br /><br /> 如需有關偵錯支援並行執行階段的詳細資訊，請參閱[使用工作視窗](/visualstudio/debugger/using-the-tasks-window)，[使用平行堆疊視窗](/visualstudio/debugger/using-the-parallel-stacks-window)，和[逐步解說：偵錯平行應用程式](/visualstudio/debugger/walkthrough-debugging-a-parallel-application)。|

## <a name="when-not-to-migrate-from-openmp-to-the-concurrency-runtime"></a>不要從 OpenMP 移轉至並行執行階段的時機

下列案例說明時可能不適合移轉現有的 OpenMP 程式碼，以使用並行執行階段。

|Cases|說明|
|-----------|-----------------|
|您的應用程式已經符合您的需求。|如果您滿意應用程式的效能和目前的偵錯支援，可能不適合移轉。|
|平行迴圈主體執行一些工作。|並行執行階段工作排程器的額外負荷可能會無法克服以平行方式執行迴圈主體，尤其是當迴圈主體是相對較小的優點。|
|您的應用程式是以 c 撰寫|並行執行階段會使用許多 c + + 功能，因為它可能不適合時您無法撰寫程式碼，讓 C 應用程式以充分利用它。|

## <a name="related-topics"></a>相關主題

[如何：轉換 OpenMP parallel for 迴圈以使用並行執行階段](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)

指定使用 OpenMP 基本迴圈[平行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)並[如](../../parallel/openmp/reference/for-openmp.md)指示詞，示範如何將它轉換成使用並行執行階段[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法。

[如何：轉換使用取消的 OpenMP 迴圈以使用並行執行階段](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)<br/>
指定 OpenMP[平行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[如](../../parallel/openmp/reference/for-openmp.md)迴圈，不需要所有的反覆項目，若要執行，示範如何將它轉換成使用並行執行階段取消機制。

[如何：轉換使用例外狀況處理的 OpenMP 迴圈以使用並行執行階段](../../parallel/concrt/convert-an-openmp-loop-that-uses-exception-handling.md)<br/>
指定 OpenMP[平行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[如](../../parallel/openmp/reference/for-openmp.md)執行例外狀況處理的迴圈會示範如何將它轉換成使用並行執行階段例外狀況處理機制。

[如何：轉換使用削減變數的 OpenMP 迴圈以使用並行執行階段](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)<br/>
指定 OpenMP[平行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[如](../../parallel/openmp/reference/for-openmp.md)使用迴圈[減少](../../parallel/openmp/reference/reduction.md)子句中，示範如何將它轉換成使用並行執行階段。

## <a name="see-also"></a>另請參閱

[並行執行階段](../../parallel/concrt/concurrency-runtime.md)<br/>
[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)<br/>
[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)
