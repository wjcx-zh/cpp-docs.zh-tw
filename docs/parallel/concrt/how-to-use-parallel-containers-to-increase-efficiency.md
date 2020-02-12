---
title: 如何：使用平行容器提高效率
ms.date: 11/04/2016
helpviewer_keywords:
- increasing efficiency with parallel containers [Concurrency Runtime]
- concurrent_queue class, examples
- concurrent_vector class, examples
ms.assetid: bd00046d-e9b6-4ae1-b661-3995f671b867
ms.openlocfilehash: cd120d1fbe0f73ed0974efda5a1aa643a1afde9d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143003"
---
# <a name="how-to-use-parallel-containers-to-increase-efficiency"></a>如何：使用平行容器提高效率

本主題說明如何使用平行容器，以平行方式有效率地儲存和存取資料。

範例程式碼會以平行方式計算質數和 Carmichael 數位的集合。 然後，針對每個 Carmichael 的數位，程式碼會計算該數位的主要因素。

## <a name="example"></a>範例

下列範例顯示 `is_prime` 函式，它會判斷輸入值是否為質數，以及判斷輸入值是否為 Carmichael 數位的 `is_carmichael` 函數。

[!code-cpp[concrt-carmichael-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_1.cpp)]

## <a name="example"></a>範例

下列範例會使用 `is_prime` 和 `is_carmichael` 函數來計算質數和 Carmichael 數位的集合。 此範例會使用[concurrency：:p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)和[concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法，以平行方式計算每個集合。 如需平行演算法的詳細資訊，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。

這個範例會使用[concurrency：： concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)物件來保存 Carmichael 數位的集合，因為它稍後會使用該物件做為工作佇列。 它會使用[concurrency：： concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)物件來保留質數集合，因為它稍後會逐一查看此集合以尋找主要因素。

[!code-cpp[concrt-carmichael-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_2.cpp)]

## <a name="example"></a>範例

下列範例顯示 `prime_factors_of` 函式，此函式會使用試用除法來尋找指定值的所有質數。

此函式會使用[concurrency：:p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)演算法來逐一查看質數集合。 `concurrent_vector` 物件可讓平行迴圈同時在結果中加入主要因素。

[!code-cpp[concrt-carmichael-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_3.cpp)]

## <a name="example"></a>範例

這個範例會藉由呼叫 `prime_factors_of` 函式來計算其主要因素，以處理 Carmichael 數位佇列中的每個元素。 它會使用工作組來平行執行此工作。 如需工作組的詳細資訊，請參閱工作[平行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)處理原則。

如果該數位具有四個以上的主要因素，則此範例會列印每個 Carmichael 數位的主要因素。

[!code-cpp[concrt-carmichael-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_4.cpp)]

## <a name="example"></a>範例

下列程式碼顯示完整的範例，其使用平行容器來計算 Carmichael 數位的主要因素。

[!code-cpp[concrt-carmichael-primes#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_5.cpp)]

這個範例會產生下列範例輸出。

```Output
Prime factors of 9890881 are: 7 11 13 41 241.
Prime factors of 825265 are: 5 7 17 19 73.
Prime factors of 1050985 are: 5 13 19 23 37.
```

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為 `carmichael-primes.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl/EHsc carmichael-primes .cpp**

## <a name="see-also"></a>另請參閱

[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[工作平行處理](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[concurrent_vector 類別](../../parallel/concrt/reference/concurrent-vector-class.md)<br/>
[concurrent_queue 類別](../../parallel/concrt/reference/concurrent-queue-class.md)<br/>
[parallel_invoke 函式](reference/concurrency-namespace-functions.md#parallel_invoke)<br/>
[parallel_for 函式](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[task_group 類別](reference/task-group-class.md)
