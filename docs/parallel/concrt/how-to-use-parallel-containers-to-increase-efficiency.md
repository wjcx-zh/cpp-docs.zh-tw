---
title: 如何： 使用平行容器提高效率 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- increasing efficiency with parallel containers [Concurrency Runtime]
- concurrent_queue class, examples
- concurrent_vector class, examples
ms.assetid: bd00046d-e9b6-4ae1-b661-3995f671b867
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71a4aee5664864b5a9c803ac5048e8e5b5eacf0a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383307"
---
# <a name="how-to-use-parallel-containers-to-increase-efficiency"></a>如何：使用平行容器提高效率

本主題說明如何使用平行容器來有效率地儲存及存取資料，以平行方式。

範例程式碼會計算一組質數和 Carmichael 數字，以平行方式。 然後，每個 Carmichael 號碼，程式碼會計算該數字的主要因素。

## <a name="example"></a>範例

下列範例所示`is_prime`函式，判斷輸入的值是否是質數，而`is_carmichael`函式，判斷輸入的值是否為 Carmichael 數字。

[!code-cpp[concrt-carmichael-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_1.cpp)]

## <a name="example"></a>範例

下列範例會使用`is_prime`和`is_carmichael`函式來計算的質數和 Carmichael 數字。 此範例會使用[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)並[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法來計算每個設定以平行方式。 如需平行演算法的詳細資訊，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。

這個範例會使用[concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)物件來保存 Carmichael 組數字，因為它稍後將該物件做為工作佇列。 它會使用[concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)物件來保存一組質數，因為它將會稍後再逐一查看這個設定為尋找主要因素。

[!code-cpp[concrt-carmichael-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_2.cpp)]

## <a name="example"></a>範例

下列範例所示`prime_factors_of`函式，以使用試用版的除法尋找指定值的所有主要的因素。

此函式會使用[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)演算法，以逐一查看集合的質數。 `concurrent_vector`物件可讓平行迴圈，同時加入結果中的主要因素。

[!code-cpp[concrt-carmichael-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_3.cpp)]

## <a name="example"></a>範例

此範例會處理 Carmichael 數字的佇列中的每個項目，藉由呼叫`prime_factors_of`函式來計算其主要的因素。 它會使用工作群組以平行方式執行這項工作。 如需工作群組的詳細資訊，請參閱[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

此範例會列印 Carmichael 中的每個數字的主要因素，如果該數字有四個以上的主要因素。

[!code-cpp[concrt-carmichael-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_4.cpp)]

## <a name="example"></a>範例

下列程式碼顯示完整的範例中，使用平行容器計算 Carmichael 數字的主要因素。

[!code-cpp[concrt-carmichael-primes#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_5.cpp)]

此範例會產生下列輸出範例。

```Output
Prime factors of 9890881 are: 7 11 13 41 241.
Prime factors of 825265 are: 5 7 17 19 73.
Prime factors of 1050985 are: 5 13 19 23 37.
```

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`carmichael-primes.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc carmichael primes.cpp**

## <a name="see-also"></a>另請參閱

[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[concurrent_vector 類別](../../parallel/concrt/reference/concurrent-vector-class.md)<br/>
[concurrent_queue 類別](../../parallel/concrt/reference/concurrent-queue-class.md)<br/>
[parallel_invoke 函式](reference/concurrency-namespace-functions.md#parallel_invoke)<br/>
[parallel_for 函式](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[task_group 類別](reference/task-group-class.md)
