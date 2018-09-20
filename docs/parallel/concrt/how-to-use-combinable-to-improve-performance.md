---
title: 如何： 使用 combinable 改善效能 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- combinable class, example
- improving parallel performance with combinable [Concurrency Runtime]
ms.assetid: fa730580-1c94-4b2d-8aec-57c91dc0497e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 22425ac212ee2bfb52354044b1a6193b6a9cd11a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432084"
---
# <a name="how-to-use-combinable-to-improve-performance"></a>如何：使用可組合的類別改善效能

此範例示範如何使用[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)類別來計算中的數字的總和[std:: array](../../standard-library/array-class-stl.md)是質數的物件。 `combinable`類別可以藉由消除共用的狀態來改善效能。

> [!TIP]
>  在某些情況下，平行對應 ([concurrency:: parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform))，並減少 ([並行:: parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce)) 可透過提供效能改進`combinable`。 如需範例，使用對應並減少作業以產生與此範例中相同的結果，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="example"></a>範例

下列範例會使用[std:: accumulate](../../standard-library/numeric-functions.md#accumulate)函式來計算陣列中的項目屬於質數的總和。 在此範例中，`a`已`array`物件和`is_prime`函式會判斷其輸入的值是否為質數。

[!code-cpp[concrt-parallel-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_1.cpp)]

## <a name="example"></a>範例

下列範例會示範最單純的方法，來平行處理上一個範例。 這個範例會使用[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)演算法處理平行陣列並[concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)來同步存取的物件`prime_sum`變數. 此範例不會調整，因為每個執行緒必須等待資源變成可用的共用資源。

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_2.cpp)]

## <a name="example"></a>範例

下列範例會使用`combinable`物件，以改善效能的上一個範例。 此範例中就不需要同步處理物件;它會延展，因為`combinable`物件可讓每個執行緒以獨立執行其工作。

A`combinable`物件通常會在兩個步驟。 第一次，產生一系列的細部運算，藉由以平行方式執行工作。 接下來，結合 （或減少） 成最終的結果計算。 這個範例會使用[concurrency::combinable::local](reference/combinable-class.md#local)方法，以取得區域總和的參考。 然後它會使用[concurrency::combinable::combine](reference/combinable-class.md#combine)方法並[std:: plus](../../standard-library/plus-struct.md)結合成最終結果這些區域運算的物件。

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_3.cpp)]

## <a name="example"></a>範例

下列完整的範例會在循序和平行計算質數數值的總和。 此範例會列印至主控台，才能執行這兩項計算的時間。

[!code-cpp[concrt-parallel-sum-of-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_4.cpp)]

下列範例輸出適用於具有四個處理器的電腦。

```Output
1709600813
serial time: 6178 ms

1709600813
parallel time: 1638 ms
```

## <a name="compiling-the-code"></a>編譯程式碼

若要編譯程式碼，將它複製然後將它貼在 Visual Studio 專案中，或將它貼在檔案，稱為`parallel-sum-of-primes.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc 平行-加總-的-primes.cpp**

## <a name="robust-programming"></a>穩固程式設計

如需範例，使用對應並減少作業以產生相同的結果，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="see-also"></a>另請參閱

[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable 類別](../../parallel/concrt/reference/combinable-class.md)<br/>
[critical_section 類別](../../parallel/concrt/reference/critical-section-class.md)
