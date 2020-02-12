---
title: 如何：轉換 OpenMP parallel for 迴圈來使用並行執行階段
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, parallel for loops
- converting from OpenMP to the Concurrency Runtime, parallel loops
- parallel for loops, converting from OpenMP to the Concurrency Runtime
- parallel loops, converting from OpenMP to the Concurrency Runtime
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
ms.openlocfilehash: 2d96ba23582368fe72e61003823826a6f3ab807a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141756"
---
# <a name="how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime"></a>如何：轉換 OpenMP parallel for 迴圈來使用並行執行階段

這個範例示範如何轉換使用 OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)和[for](../../parallel/openmp/reference/for-openmp.md)指示詞的基本迴圈，以使用並行執行階段[Concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法。

## <a name="example---prime-count"></a>範例-質數計數

這個範例會使用 OpenMP 和並行執行階段來計算隨機值陣列中的質數計數。

[!code-cpp[concrt-openmp#1](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_1.cpp)]

此範例會產生下列輸出。

```Output
Using OpenMP...
found 107254 prime numbers.
Using the Concurrency Runtime...
found 107254 prime numbers.
```

`parallel_for` 演算法和 OpenMP 3.0 允許索引類型為帶正負號的整數類資料類型或不帶正負號的整數類資料類型。 `parallel_for` 演算法也會確保指定的範圍不會溢位帶正負號的類型。 OpenMP 版本2.0 和2.5 僅允許帶正負號的整數索引類型。 OpenMP 也不會驗證索引範圍。

這個使用並行執行階段的範例版本也會使用[Concurrency：：可組合](../../parallel/concrt/reference/combinable-class.md)物件來取代不可部分[完成的指示](../../parallel/openmp/reference/atomic.md)詞，以遞增計數器值，而不需要同步處理。

如需 `parallel_for` 和其他平行演算法的詳細資訊，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。 如需 `combinable` 類別的詳細資訊，請參閱[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="example---use-stdarray"></a>範例-使用 std：： array

這個範例會修改上一個，以對[std：： array](../../standard-library/array-class-stl.md)物件採取動作，而不是在原生陣列上執行。 因為 OpenMP 版本2.0 和2.5 只允許在 `parallel_for` 結構中有帶正負號的整數索引類型，所以您無法使用反覆運算器以C++平行方式存取標準程式庫容器的元素。 平行模式程式庫（PPL）提供[concurrency：:p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)演算法，它會以平行方式在反復執行的容器（例如C++標準程式庫所提供的）上執行工作。 它會使用 `parallel_for` 演算法所使用的相同分割邏輯。 `parallel_for_each` 演算法與C++標準程式庫[std：： for_each](../../standard-library/algorithm-functions.md#for_each)演算法相似，不同之處在于 `parallel_for_each` 演算法會同時執行這些工作。

[!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為 `concrt-omp-count-primes.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl/EHsc/openmp concrt-omp-count-primes .cpp**

## <a name="see-also"></a>另請參閱

[從 OpenMP 移轉至並行執行階段](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)
