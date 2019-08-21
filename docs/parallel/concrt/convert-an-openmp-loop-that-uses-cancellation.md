---
title: HOW TO：轉換使用取消的 OpenMP 迴圈, 以使用並行執行階段
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, cancellation
- cancellation, converting from OpenMP to the Concurrency Runtime
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
ms.openlocfilehash: df55a58617b802f24e4caf13784ac080222b93bc
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631521"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-cancellation-to-use-the-concurrency-runtime"></a>作法：轉換使用取消的 OpenMP 迴圈, 以使用並行執行階段

某些平行迴圈不需要執行所有的反復專案。 例如, 搜尋值的演算法可以在找到值之後終止。 OpenMP 不會提供機制來中斷平行迴圈。 不過, 您可以使用布林值或旗標來啟用迴圈的反復專案, 以指出已找到該方案。 並行執行階段所提供的功能, 可讓一個工作取消其他尚未啟動的工作。

這個範例示範如何轉換 OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../../parallel/openmp/reference/for-openmp.md)迴圈, 讓所有反覆運算都不需要執行, 就能使用並行執行階段取消機制。

## <a name="example"></a>範例

這個範例會同時使用 OpenMP 和並行執行階段來執行[std:: any_of](../../standard-library/algorithm-functions.md#any_of)演算法的平行版本。 這個範例的 OpenMP 版本使用旗標來協調條件已符合的所有平行迴圈反覆運算。 使用並行執行階段的版本會使用[Concurrency:: structured_task_group:: cancel](reference/structured-task-group-class.md#cancel)方法, 在符合條件時停止整體作業。

[!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]

此範例會產生下列輸出。

```Output
Using OpenMP...
9114046 is in the array.
Using the Concurrency Runtime...
9114046 is in the array.
```

在使用 OpenMP 的版本中, 迴圈的所有反覆運算都會執行, 即使已設定旗標也一樣。 此外, 如果工作有任何子工作, 則此旗標也必須可供這些子工作使用, 以傳達取消作業。 在並行執行階段中, 當工作組取消時, 執行時間會取消整個工作樹狀結構, 包括子工作。 [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)演算法會使用工作來執行工作。 因此, 當迴圈的一個反復專案取消根工作時, 也會取消整個計算的樹狀結構。 取消工作的樹狀結構時, 執行時間不會啟動新的工作。 不過, 執行時間允許已啟動的工作完成。 因此, 在`parallel_for_each`演算法的案例中, 作用中迴圈反復專案可以清除其資源。

在此範例的兩個版本中, 如果陣列包含多個要搜尋的值複本, 多個迴圈反覆運算可以同時設定結果, 並取消整體作業。 如果您的問題需要只有一個工作在符合條件時執行工作, 您可以使用同步處理原始物件 (例如重要區段)。

您也可以使用例外狀況處理來取消使用 PPL 的工作。 如需取消的詳細資訊, 請參閱[PPL 中的取消](cancellation-in-the-ppl.md)。

如需`parallel_for_each`和其他平行演算法的詳細資訊, 請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼, 並將它貼入 Visual Studio 專案中, 或貼入名`concrt-omp-parallel-any-of.cpp`為的檔案中, 然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

**cl/EHsc/openmp concrt-omp-parallel-any-of .cpp**

## <a name="see-also"></a>另請參閱

[從 OpenMP 移轉至並行執行階段](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[PPL 中的取消](cancellation-in-the-ppl.md)<br/>
[平行演算法](../../parallel/concrt/parallel-algorithms.md)
