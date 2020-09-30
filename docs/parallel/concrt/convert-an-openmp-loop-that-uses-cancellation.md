---
title: 如何：轉換使用取消的 OpenMP 迴圈來使用並行執行階段
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, cancellation
- cancellation, converting from OpenMP to the Concurrency Runtime
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
ms.openlocfilehash: adde6decc086b883c50e52d12e388197e185fb39
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505946"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-cancellation-to-use-the-concurrency-runtime"></a>如何：轉換使用取消的 OpenMP 迴圈來使用並行執行階段

某些平行迴圈不需要執行所有的反覆運算。 例如，搜尋值的演算法可以在找到值之後終止。 OpenMP 未提供中斷平行迴圈的機制。 不過，您可以使用布林值（或旗標）來啟用迴圈的反覆運算，以表示已找到方案。 並行執行階段提供的功能可讓一項工作取消尚未啟動的其他工作。

這個範例會示範如何轉換不需要執行所有反復專案的 OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp) 迴圈，以使用並行執行階段取消機制。

## <a name="example"></a>範例

這個範例會使用 OpenMP 和並行執行階段來執行 [std：： any_of](../../standard-library/algorithm-functions.md#any_of) 演算法的平行版本。 此範例的 OpenMP 版本會使用旗標，在符合條件的所有平行迴圈反覆運算之間進行協調。 使用並行執行階段的版本會使用 [Concurrency：： structured_task_group：： cancel](reference/structured-task-group-class.md#cancel) 方法，在符合條件時停止整體作業。

[!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]

此範例會產生下列輸出。

```Output
Using OpenMP...
9114046 is in the array.
Using the Concurrency Runtime...
9114046 is in the array.
```

在使用 OpenMP 的版本中，即使已設定旗標，也會執行迴圈的所有反覆運算。 此外，如果工作有任何子工作，則此旗標也必須可供那些子工作使用，以傳達取消作業。 在並行執行階段中，當工作組取消時，執行時間會取消整個工作樹狀結構，包括子工作。 [Concurrency：:p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)演算法會使用工作來執行工作。 因此，當迴圈的某個反復專案取消根工作時，也會取消整個計算樹狀結構。 當工作樹狀結構取消時，執行時間不會啟動新的工作。 不過，執行時間允許已開始完成的工作。 因此，在演算法的案例中 `parallel_for_each` ，作用中迴圈反復專案可以清除其資源。

在此範例的這兩個版本中，如果陣列包含要搜尋之值的多個複本，則多個迴圈反復專案可以同時設定結果並取消整體作業。 您可以使用同步處理原始物件，例如重要區段，如果您的問題要求只有一個工作在符合條件時才執行工作。

您也可以使用例外狀況處理來取消使用 PPL 的工作。 如需取消的詳細資訊，請參閱 [PPL 中的取消](cancellation-in-the-ppl.md)。

如需 `parallel_for_each` 和其他平行演算法的詳細資訊，請參閱 [平行演算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="compiling-the-code"></a>編譯程式碼

請複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為的檔案中， `concrt-omp-parallel-any-of.cpp` 然後在 Visual Studio 命令提示字元視窗中執行下列命令。

> **cl.exe/EHsc/openmp concrt-omp-parallel-any-of .cpp**

## <a name="see-also"></a>另請參閱

[從 OpenMP 移轉至並行執行階段](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[PPL 中的取消](cancellation-in-the-ppl.md)<br/>
[平行演算法](../../parallel/concrt/parallel-algorithms.md)
