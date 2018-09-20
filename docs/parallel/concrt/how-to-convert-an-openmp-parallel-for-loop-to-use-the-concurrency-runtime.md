---
title: 如何： 轉換 OpenMP parallel for 迴圈來使用並行執行階段 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, parallel for loops
- converting from OpenMP to the Concurrency Runtime, parallel loops
- parallel for loops, converting from OpenMP to the Concurrency Runtime
- parallel loops, converting from OpenMP to the Concurrency Runtime
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5295a7e38ef511cd2703961ffe8fe6f22faa74ae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407955"
---
# <a name="how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime"></a>如何：轉換 OpenMP parallel for 迴圈來使用並行執行階段

這個範例示範如何將基本迴圈使用 OpenMP[平行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)並[的](../../parallel/openmp/reference/for-openmp.md)來使用並行執行階段指示詞[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法。

## <a name="example"></a>範例

此範例會使用 OpenMP 與並行執行階段計算隨機值的陣列中質數的計數。

[!code-cpp[concrt-openmp#1](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_1.cpp)]

此範例會產生下列輸出。

```Output
Using OpenMP...
found 107254 prime numbers.
Using the Concurrency Runtime...
found 107254 prime numbers.
```

`parallel_for`演算法和 OpenMP 3.0 可讓索引類型為帶正負號的整數類資料類型或不帶正負號的整數類資料類型。 `parallel_for`演算法也可確保指定的範圍不帶正負號的類型溢位。 OpenMP 版本 2.0 和 2.5 可讓帶正負號的整數索引類型。 OpenMP 也不會驗證的索引範圍。

此範例是使用並行執行階段的版本也會使用[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)物件的位置[不可部分完成](../../parallel/openmp/reference/atomic.md)指示詞，以遞增的計數器值，而不需要同步處理。

如需詳細資訊`parallel_for`和其他平行演算法，請參閱 <<c2> [ 平行演算法](../../parallel/concrt/parallel-algorithms.md)。 如需詳細資訊`combinable`類別，請參閱[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="example"></a>範例

此範例會修改前一個採取行動[std:: array](../../standard-library/array-class-stl.md)物件而不是原生陣列。 因為 OpenMP 版本 2.0 和 2.5 允許帶正負號整數類資料的索引類型只能在`parallel_for`建構 」、 「 無法使用迭代器，來存取以平行方式的 c + + 標準程式庫容器的項目。 平行模式程式庫 (PPL) 提供[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)執行的工作，以平行方式反覆執行的容器，例如 c + + 標準程式庫所提供的演算法。 它會使用相同的資料分割邏輯的`parallel_for`演算法使用。 `parallel_for_each`演算法類似於 c + + 標準程式庫[std:: for_each](../../standard-library/algorithm-functions.md#for_each)演算法，不同之處在於`parallel_for_each`演算法同時執行的工作。

[!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`concrt-omp-count-primes.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc /openmp concrt-omp-計數-primes.cpp**

## <a name="see-also"></a>另請參閱

[從 OpenMP 移轉至並行執行階段](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)

