---
title: 如何： 撰寫 parallel_for_each 迴圈 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- writing a parallel_for_each loop [Concurrency Runtime]
- parallel_for_each function, example
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c68afa77c46e4d57ef01984b44ecb6f4951494a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427078"
---
# <a name="how-to-write-a-parallelforeach-loop"></a>如何：撰寫 parallel_for_each 迴圈

此範例示範如何使用[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)演算法來計算中質數的計數[std:: array](../../standard-library/array-class-stl.md)以平行方式的物件。

## <a name="example"></a>範例

下列範例會計算陣列中質數的計數兩次。 此範例會先使用[std:: for_each](../../standard-library/algorithm-functions.md#for_each)循序計算計數的演算法。 然後此範例使用`parallel_for_each`演算法以平行方式執行相同的工作。 這個範例也會將執行這兩項計算所需的時間列印到主控台。

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

若要編譯程式碼，將它複製然後將它貼在 Visual Studio 專案中，或將它貼在檔案，稱為`parallel-count-primes.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc 平行計數 primes.cpp**

## <a name="robust-programming"></a>穩固程式設計

此範例會傳遞至 lambda 運算式`parallel_for_each`演算法會使用`InterlockedIncrement`函式可讓同時遞增計數器迴圈的平行反覆項目。 如果您使用函式，例如`InterlockedIncrement`進行同步處理共用資源的存取權，您可以在程式碼中呈現效能瓶頸。 您可以使用無鎖定同步處理機制，比方說，則[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)類別，以消除同時存取共用資源。 如需使用的範例`combinable`類別以這種方式，請參閱[如何： 使用 combinable 改善效能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)。

## <a name="see-also"></a>另請參閱

[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for_each 函式](reference/concurrency-namespace-functions.md#parallel_for_each)

