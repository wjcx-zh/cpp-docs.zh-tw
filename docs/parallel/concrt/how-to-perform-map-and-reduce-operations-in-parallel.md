---
title: 如何：平行執行對應和縮減作業
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_transform function, example
- parallel map and reduce, example
- parallel_reduce function, example
ms.assetid: 9d19fac0-4ab6-4380-a375-3b18eeb87720
ms.openlocfilehash: 599e46c05a91a1f2ea6e317fe024d3c98a78977f
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141713"
---
# <a name="how-to-perform-map-and-reduce-operations-in-parallel"></a>如何：平行執行對應和縮減作業

這個範例示範如何使用[concurrency：:p arallel_transform](reference/concurrency-namespace-functions.md#parallel_transform)和 concurrency： [:p arallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce)演算法和[concurrency：： concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)類別來計算檔案中文字的出現次數。

*對應*作業會將函式套用至序列中的每個值。 「*減少*」作業會將序列的元素結合成一個值。 您可以使用C++標準程式庫[std：： transform](../../standard-library/algorithm-functions.md#transform)和[std：：累積](../../standard-library/numeric-functions.md#accumulate)函數來執行對應和縮減作業。 不過，若要針對許多問題改善效能，您可以使用 `parallel_transform` 演算法以平行方式執行對應作業，以及使用 `parallel_reduce` 演算法以平行方式執行縮減作業。 在某些情況下，您可以使用 `concurrent_unordered_map` 在一個作業中執行對應和縮減。

## <a name="example"></a>範例

下列範例會計算文字在檔案中的出現次數。 它使用[std：： vector](../../standard-library/vector-class.md)來表示兩個檔案的內容。 對應作業會計算每個向量中每個字的出現次數。 縮減作業會累計兩個向量的字數統計。

[!code-cpp[concrt-parallel-map-reduce#1](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_1.cpp)]

## <a name="compiling-the-code"></a>編譯程式碼

若要編譯器代碼，請複製該程式碼，然後將它貼入 Visual Studio 專案中，或貼入名為 `parallel-map-reduce.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl/EHsc parallel-map-reduce.cpp .cpp**

## <a name="robust-programming"></a>最佳化程式設計

在這個範例中，您可以使用在 concurrent_unordered_map.h中定義的 `concurrent_unordered_map` 類別，在一個作業中執行對應和縮減。

[!code-cpp[concrt-parallel-map-reduce#2](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_2.cpp)]

一般而言，您只會平行處理外部或內部迴圈。 如果您的檔案數相當少，而且每個檔案包含許多單字，則請平行處理內部迴圈。 如果您的檔案數相當多，而且每個檔案包含少數單字，則請平行處理外部迴圈。

## <a name="see-also"></a>另請參閱

[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_transform 函式](reference/concurrency-namespace-functions.md#parallel_transform)<br/>
[parallel_reduce 函式](reference/concurrency-namespace-functions.md#parallel_reduce)<br/>
[concurrent_unordered_map 類別](../../parallel/concrt/reference/concurrent-unordered-map-class.md)
