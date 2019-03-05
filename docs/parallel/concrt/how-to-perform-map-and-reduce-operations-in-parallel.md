---
title: HOW TO：執行對應和縮減作業以平行方式
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_transform function, example
- parallel map and reduce, example
- parallel_reduce function, example
ms.assetid: 9d19fac0-4ab6-4380-a375-3b18eeb87720
ms.openlocfilehash: ba3ffb5cdae7dcc6f108f005fab33f9a1fee6a6f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258654"
---
# <a name="how-to-perform-map-and-reduce-operations-in-parallel"></a>HOW TO：執行對應和縮減作業以平行方式

此範例示範如何使用[concurrency:: parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform)並[concurrency:: parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce)演算法和[concurrency:: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)類別，以計算文字在檔案中的出現次數。

A*地圖*作業函式套用至序列中每個值。 A*減少*作業結合成單一值序列的元素。 您可以使用 c + + 標準程式庫[std:: transform](../../standard-library/algorithm-functions.md#transform)並[std:: accumulate](../../standard-library/numeric-functions.md#accumulate)函式來執行對應和縮減作業。 不過，若要針對許多問題改善效能，您可以使用 `parallel_transform` 演算法以平行方式執行對應作業，以及使用 `parallel_reduce` 演算法以平行方式執行縮減作業。 在某些情況下，您可以使用 `concurrent_unordered_map` 在一個作業中執行對應和縮減。

## <a name="example"></a>範例

下列範例會計算文字在檔案中的出現次數。 它會使用[std:: vector](../../standard-library/vector-class.md)來表示兩個檔案的內容。 對應作業會計算每個向量中每個字的出現次數。 縮減作業會累計兩個向量的字數統計。

[!code-cpp[concrt-parallel-map-reduce#1](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_1.cpp)]

## <a name="compiling-the-code"></a>編譯程式碼

若要編譯程式碼，將它複製然後將它貼在 Visual Studio 專案中，或將它貼在檔案，稱為`parallel-map-reduce.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc 平行對應 reduce.cpp**

## <a name="robust-programming"></a>穩固程式設計

在這個範例中，您可以使用在 concurrent_unordered_map.h中定義的 `concurrent_unordered_map` 類別，在一個作業中執行對應和縮減。

[!code-cpp[concrt-parallel-map-reduce#2](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_2.cpp)]

一般而言，您只會平行處理外部或內部迴圈。 如果您的檔案數相當少，而且每個檔案包含許多單字，則請平行處理內部迴圈。 如果您的檔案數相當多，而且每個檔案包含少數單字，則請平行處理外部迴圈。

## <a name="see-also"></a>另請參閱

[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_transform 函式](reference/concurrency-namespace-functions.md#parallel_transform)<br/>
[parallel_reduce 函式](reference/concurrency-namespace-functions.md#parallel_reduce)<br/>
[concurrent_unordered_map 類別](../../parallel/concrt/reference/concurrent-unordered-map-class.md)
