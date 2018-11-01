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
ms.openlocfilehash: e72d99cb1b9168e3de1e109d93c163e21cb7fad7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440153"
---
# <a name="how-to-use-parallelinvoke-to-write-a-parallel-sort-routine"></a>如何：使用 parallel_invoke 撰寫平行排序常式

本文件說明如何使用[parallel_invoke](../../parallel/concrt/parallel-algorithms.md#parallel_invoke)演算法，以改善 bitonic 排序演算法的效能。 雙調排序演算法以遞迴方式會將輸入的序列分成較小的已排序分割區。 Bitonic 排序演算法可以以平行方式執行，因為每個分割區作業無關的所有其他作業。

雖然 bitonic 排序的範例*排序網路*，排序的輸入序列的所有組合，此範例都排序的序列的長度為 2 的乘冪。

> [!NOTE]
>  這個範例會使用平行排序常式做為說明。 您也可以使用 PPL 提供的內建排序演算法： [concurrency:: parallel_sort](reference/concurrency-namespace-functions.md#parallel_sort)， [concurrency:: parallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort)，和[concurrency::parallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort)。 如需詳細資訊，請參閱 <<c0> [ 平行演算法](../../parallel/concrt/parallel-algorithms.md)。

##  <a name="top"></a> 章節

本文件說明下列工作：

- [以序列方式執行雙調排序](#serial)

- [以平行方式使用 parallel_invoke 執行雙調排序](#parallel)

##  <a name="serial"></a> 以序列方式執行雙調排序

下列範例顯示 bitonic 排序演算法的序列版本。 `bitonic_sort`函式會將序列分割成兩個資料分割、 排序相反的方向，這些資料分割，然後合併結果。 此函式會呼叫本身兩次以遞迴方式來排序每個資料分割。

[!code-cpp[concrt-parallel-bitonic-sort#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_1.cpp)]

[[靠上](#top)]

##  <a name="parallel"></a> 以平行方式使用 parallel_invoke 執行雙調排序

本章節描述如何使用`parallel_invoke`以平行方式執行 bitonic 排序演算法的演算法。

### <a name="procedures"></a>程序

##### <a name="to-perform-the-bitonic-sort-algorithm-in-parallel"></a>若要以平行方式執行 bitonic 排序演算法

1. 新增`#include`指示詞標頭檔 ppl.h。

[!code-cpp[concrt-parallel-bitonic-sort#10](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_2.cpp)]

1. 新增`using`指示詞`concurrency`命名空間。

[!code-cpp[concrt-parallel-bitonic-sort#11](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_3.cpp)]

1. 建立新的函式，呼叫`parallel_bitonic_mege`，它會使用`parallel_invoke`演算法來合併平行序列，如果沒有足夠的工作數量。 否則，呼叫`bitonic_merge`循序合併的序列。

[!code-cpp[concrt-parallel-bitonic-sort#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_4.cpp)]

1. 執行程序，類似於上一個步驟中，但在`bitonic_sort`函式。

[!code-cpp[concrt-parallel-bitonic-sort#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_5.cpp)]

1. 建立的多載的版本`parallel_bitonic_sort`排序的陣列，以遞增順序的函式。

[!code-cpp[concrt-parallel-bitonic-sort#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_6.cpp)]

`parallel_invoke`演算法呼叫的內容上執行一個工作序列的最後一個來減少額外負荷。 例如，在`parallel_bitonic_sort`函式的第一個工作執行於不同的內容，以及呼叫的內容上執行的第二項工作。

[!code-cpp[concrt-parallel-bitonic-sort#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_7.cpp)]

序號和 bitonic 排序演算法的平行版本，則會執行下列完整的範例。 範例也會列印到主控台，才能執行每個計算的時間。

[!code-cpp[concrt-parallel-bitonic-sort#8](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_8.cpp)]

下列範例輸出適用於具有四個處理器的電腦。

```Output
serial time: 4353
parallel time: 1248
```

[[靠上](#top)]

## <a name="compiling-the-code"></a>編譯程式碼

若要編譯程式碼，將它複製然後將它貼在 Visual Studio 專案中，或將它貼在檔案，稱為`parallel-bitonic-sort.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc 平行 bitonic sort.cpp**

## <a name="robust-programming"></a>穩固程式設計

這個範例會使用`parallel_invoke`演算法，而非[concurrency:: task_group](reference/task-group-class.md)類別，因為每個工作群組的存留期不超過函式。 我們建議您改用`parallel_invoke`您可以因為它具有較少執行額外負荷比`task group`物件，並因此可讓您撰寫效能更好的程式碼。

僅當沒有足夠的工作来執行時，有些演算法的平行版本會比較好。 例如，`parallel_bitonic_merge`函式會呼叫序列版， `bitonic_merge`，如果序列中具有 500 或更少的項目。 您也可以規劃整體排序策略工作數量為基礎。 比方說，它可能會更有效率使用快速排序演算法的序列版本，如果陣列包含少於 500 個項目，如下列範例所示：

[!code-cpp[concrt-parallel-bitonic-sort#9](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_9.cpp)]

如同任何平行處理演算法，我們建議您設定檔，並調整為適當的程式碼。

## <a name="see-also"></a>另請參閱

[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[parallel_invoke 函式](reference/concurrency-namespace-functions.md#parallel_invoke)

