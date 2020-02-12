---
title: 如何：撰寫 parallel_for_each 迴圈
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for_each loop [Concurrency Runtime]
- parallel_for_each function, example
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
ms.openlocfilehash: 10c281b7db92e2706b20a1c7377fcdb9d924152d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141879"
---
# <a name="how-to-write-a-parallel_for_each-loop"></a>如何：撰寫 parallel_for_each 迴圈

這個範例示範如何使用[concurrency：:p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)演算法，以平行方式計算[std：： array](../../standard-library/array-class-stl.md)物件中的質數計數。

## <a name="example"></a>範例

下列範例會計算陣列中的質數計數兩次。 此範例會先使用[std：： for_each](../../standard-library/algorithm-functions.md#for_each)演算法，以序列方式計算計數。 然後，此範例會使用 `parallel_for_each` 演算法，以平行方式執行相同的工作。 這個範例也會將執行這兩項計算所需的時間列印到主控台。

[!code-cpp[concrt-parallel-count-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-each-loop_1.cpp)]

下列範例輸出適用於具有四個處理器的電腦。

```Output
serial version:
found 17984 prime numbers
took 6115 ms

parallel version:
found 17984 prime numbers
took 1653 ms
```

## <a name="compiling-the-code"></a>編譯程式碼

若要編譯器代碼，請複製該程式碼，然後將它貼入 Visual Studio 專案中，或貼入名為 `parallel-count-primes.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl/EHsc parallel-count-primes .cpp**

## <a name="robust-programming"></a>最佳化程式設計

範例傳遞至 `parallel_for_each` 演算法的 lambda 運算式會使用 `InterlockedIncrement` 函數來啟用迴圈的平行反覆運算，同時增加計數器。 如果您使用 `InterlockedIncrement` 之類的功能來同步處理共用資源的存取，您可以在程式碼中呈現效能瓶頸。 您可以使用無鎖定的同步處理機制，例如[concurrency：：可組合](../../parallel/concrt/reference/combinable-class.md)類別，以排除對共用資源的同時存取。 如需以這種方式使用 `combinable` 類別的範例，請參閱[如何：使用可組合的來改善效能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)。

## <a name="see-also"></a>另請參閱

[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for_each 函式](reference/concurrency-namespace-functions.md#parallel_for_each)
