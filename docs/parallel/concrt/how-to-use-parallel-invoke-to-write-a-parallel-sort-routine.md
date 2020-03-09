---
title: 如何：使用 parallel_invoke 撰寫平行排序常式
ms.date: 11/04/2016
helpviewer_keywords:
- task_handle class, example
- task_group class, example
- make_task function, example
- structured_task_group class, example
- improving parallel performance with task groups [Concurrency Runtime]
ms.assetid: 53979a2a-525d-4437-8952-f1ff85b37673
ms.openlocfilehash: 6acac3f6bc82db6e6981f83715c7ee88cfd06fbd
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855394"
---
# <a name="how-to-use-parallel_invoke-to-write-a-parallel-sort-routine"></a>如何：使用 parallel_invoke 撰寫平行排序常式

本檔說明如何使用[parallel_invoke](../../parallel/concrt/parallel-algorithms.md#parallel_invoke)演算法來改善 bitonic 排序演算法的效能。 Bitonic 排序演算法會以遞迴方式將輸入序列分成較小的已排序資料分割。 Bitonic 排序演算法可以平行執行，因為每個分割區作業都與其他所有作業無關。

雖然 bitonic 排序是排序*網路*的範例，可排序輸入序列的所有組合，但此範例會排序其長度為2乘冪的序列。

> [!NOTE]
> 這個範例會使用平行排序常式做為說明。 您也可以使用 PPL 提供的內建排序演算法： [concurrency：:p arallel_sort](reference/concurrency-namespace-functions.md#parallel_sort)、 [concurrency：:p arallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort)和[concurrency：:p arallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort)。 如需詳細資訊，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="top"></a> 章節

本檔說明下列工作：

- [連續執行 Bitonic 排序](#serial)

- [使用 parallel_invoke 平行執行 Bitonic 排序](#parallel)

## <a name="serial"></a>連續執行 Bitonic 排序

下列範例顯示 bitonic 排序演算法的序列版本。 `bitonic_sort` 函式會將序列分成兩個分割區，以相反的方向排序這些資料分割，然後合併結果。 此函式會以遞迴方式呼叫本身兩次，以排序每個分割區。

[!code-cpp[concrt-parallel-bitonic-sort#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_1.cpp)]

[[靠上](#top)]

## <a name="parallel"></a>使用 parallel_invoke 平行執行 Bitonic 排序

本節說明如何使用 `parallel_invoke` 演算法，以平行方式執行 bitonic 排序演算法。

### <a name="to-perform-the-bitonic-sort-algorithm-in-parallel"></a>若要平行執行 bitonic 排序演算法

1. 加入標頭檔 ppl. h 的 `#include` 指示詞。

[!code-cpp[concrt-parallel-bitonic-sort#10](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_2.cpp)]

1. 加入 `concurrency` 命名空間的 `using` 指示詞。

[!code-cpp[concrt-parallel-bitonic-sort#11](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_3.cpp)]

1. 建立稱為 `parallel_bitonic_mege`的新函式，此函式會使用 `parallel_invoke` 演算法，以便在有足夠的工作量時平行定序序列。 否則，請呼叫 `bitonic_merge` 來順序定序序列。

[!code-cpp[concrt-parallel-bitonic-sort#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_4.cpp)]

1. 執行與上一個步驟中類似的進程，但針對 `bitonic_sort` 函數。

[!code-cpp[concrt-parallel-bitonic-sort#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_5.cpp)]

1. 建立 `parallel_bitonic_sort` 函數的多載版本，以遞增順序排序陣列。

[!code-cpp[concrt-parallel-bitonic-sort#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_6.cpp)]

`parallel_invoke` 演算法會藉由在呼叫內容上執行最後一系列的工作，來減少額外負荷。 例如，在 `parallel_bitonic_sort` 函式中，第一個工作會在不同的內容上執行，而第二個工作則會在呼叫內容上執行。

[!code-cpp[concrt-parallel-bitonic-sort#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_7.cpp)]

下列完整範例會同時執行序列和平行版本的 bitonic 排序演算法。 此範例也會將執行每個計算所需的時間列印到主控台。

[!code-cpp[concrt-parallel-bitonic-sort#8](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_8.cpp)]

下列範例輸出適用於具有四個處理器的電腦。

```Output
serial time: 4353
parallel time: 1248
```

[[靠上](#top)]

### <a name="compiling-the-code"></a>編譯程式碼

若要編譯器代碼，請複製該程式碼，然後將它貼入 Visual Studio 專案中，或貼入名為 `parallel-bitonic-sort.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl/EHsc parallel-bitonic-sort.cpp .cpp**

## <a name="robust-programming"></a>穩固程式設計

這個範例會使用 `parallel_invoke` 演算法，而不是[concurrency：： task_group](reference/task-group-class.md)類別，因為每個工作組的存留期都不會超出函式。 我們建議您在可能的情況下使用 `parallel_invoke`，因為它的執行額外負荷比 `task group` 物件少，因此可讓您撰寫更好的執行程式碼。

只有在有足夠的工作要執行時，某些演算法的平行版本才會執行得更好。 例如，如果序列中有500或較少的元素，`parallel_bitonic_merge` 函式會呼叫序列版本，`bitonic_merge`。 您也可以根據工作量來規劃整體排序策略。 例如，如果陣列包含少於500個專案，使用快速排序演算法的序列版本可能會更有效率，如下列範例所示：

[!code-cpp[concrt-parallel-bitonic-sort#9](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_9.cpp)]

如同任何平行演算法，我們建議您在適當的情況下分析並調整程式碼。

## <a name="see-also"></a>另請參閱

[工作平行處理](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[parallel_invoke 函式](reference/concurrency-namespace-functions.md#parallel_invoke)
