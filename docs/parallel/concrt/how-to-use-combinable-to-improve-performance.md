---
title: 如何：使用可組合的類別改善效能
ms.date: 11/04/2016
helpviewer_keywords:
- combinable class, example
- improving parallel performance with combinable [Concurrency Runtime]
ms.assetid: fa730580-1c94-4b2d-8aec-57c91dc0497e
ms.openlocfilehash: db27a791b2b92102118606712db4cbd2920f9619
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142434"
---
# <a name="how-to-use-combinable-to-improve-performance"></a>如何：使用可組合的類別改善效能

這個範例會示範如何使用[concurrency：：組合](../../parallel/concrt/reference/combinable-class.md)類別來計算[std：： array](../../standard-library/array-class-stl.md)物件中的數位總和，這是質數。 `combinable` 類別藉由排除共用狀態來改善效能。

> [!TIP]
> 在某些情況下，parallel map （[concurrency：:p arallel_transform](reference/concurrency-namespace-functions.md#parallel_transform)）和減少（[concurrency：： parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce)）可以透過 `combinable`提供效能改進。 如需使用對應和減少作業產生與這個範例相同結果的範例，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="example---accumulate"></a>範例-累積

下列範例會使用[std：：累積](../../standard-library/numeric-functions.md#accumulate)函數來計算陣列中的元素總和。 在此範例中，`a` 是 `array` 物件，而 `is_prime` 函數會判斷其輸入值是否為質數。

[!code-cpp[concrt-parallel-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_1.cpp)]

## <a name="example---parallel_for_each"></a>範例-parallel_for_each

下列範例示範如何平行處理先前範例的方法。 這個範例會使用[concurrency：:p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)演算法平行處理陣列，並使用[concurrency：： critical_section](../../parallel/concrt/reference/critical-section-class.md)物件來同步存取 `prime_sum` 變數。 這個範例不會進行調整，因為每個執行緒都必須等候共用資源變成可用。

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_2.cpp)]

## <a name="example---combinable"></a>範例-組合

下列範例會使用 `combinable` 物件來改善上一個範例的效能。 這個範例不需要同步處理物件;它會進行調整，因為 `combinable` 物件可讓每個執行緒獨立執行其工作。

`combinable` 物件通常會以兩個步驟來使用。 首先，以平行方式執行工作，產生一系列的精細計算。 接下來，將計算結合（或減少）為最終結果。 這個範例會使用[concurrency：：組合：： local](reference/combinable-class.md#local)方法來取得本機總和的參考。 接著，它會使用[concurrency：：組合：：組合](reference/combinable-class.md#combine)方法和[std：:p lu](../../standard-library/plus-struct.md)物件，將本機計算結合到最終結果中。

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_3.cpp)]

## <a name="example---serial-and-parallel"></a>範例-序列和平行

下列完整範例會以序列和平行方式計算質數的總和。 此範例會將執行這兩個計算所需的時間列印到主控台。

[!code-cpp[concrt-parallel-sum-of-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_4.cpp)]

下列範例輸出適用於具有四個處理器的電腦。

```Output
1709600813
serial time: 6178 ms

1709600813
parallel time: 1638 ms
```

## <a name="compiling-the-code"></a>編譯程式碼

若要編譯器代碼，請複製該程式碼，然後將它貼入 Visual Studio 專案中，或貼入名為 `parallel-sum-of-primes.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl/EHsc parallel-sum-of-primes.cpp .cpp**

## <a name="robust-programming"></a>最佳化程式設計

如需使用對應和減少作業產生相同結果的範例，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="see-also"></a>另請參閱

[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable 類別](../../parallel/concrt/reference/combinable-class.md)<br/>
[critical_section 類別](../../parallel/concrt/reference/critical-section-class.md)
