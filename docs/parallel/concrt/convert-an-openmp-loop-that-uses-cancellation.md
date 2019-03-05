---
title: HOW TO：轉換使用並行執行階段使用取消的 OpenMP 迴圈
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, cancellation
- cancellation, converting from OpenMP to the Concurrency Runtime
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
ms.openlocfilehash: 618e93c18173bfe3e5f5b5f3058a8bb3d61e98ec
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300670"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-cancellation-to-use-the-concurrency-runtime"></a>HOW TO：轉換使用並行執行階段使用取消的 OpenMP 迴圈

部分平行迴圈不需要執行的所有反覆項目。 例如，搜尋值的演算法可以終止之後找到的值。 OpenMP 不提供一個機制來中斷平行迴圈。 不過，您可以使用布林值或旗標，若要啟用以指出已找到方案迴圈的反覆項目。 並行執行階段提供可讓取消尚未開始的其他工作的一項工作的功能。

此範例示範如何將轉換 OpenMP[平行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[如](../../parallel/openmp/reference/for-openmp.md)不需要執行的所有反覆項目來使用並行執行階段取消機制的迴圈。

## <a name="example"></a>範例

此範例中使用 OpenMP 與並行執行階段來實作平行版本[std::any_of](../../standard-library/algorithm-functions.md#any_of)演算法。 此範例中的 OpenMP 版本會使用旗標來協調之間所有平行迴圈反覆項目尚未符合條件。 使用並行執行階段的版本會使用[concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel)符合條件時停止的整體作業的方法。

[!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]

此範例會產生下列輸出。

```Output
Using OpenMP...
9114046 is in the array.
Using the Concurrency Runtime...
9114046 is in the array.
```

在使用 OpenMP 的版本，所有的反覆項目迴圈的執行，即使當旗標設定。 此外，如果工作有任何子工作，此旗標也必須可用於這些子工作，以傳達取消。 並行執行階段，當工作群組取消時，執行階段會取消整個樹狀目錄中的工作，包括子工作。 [Concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)演算法會使用工作來執行工作。 因此，當迴圈的反覆項目取消 「 根 」 工作，是也會取消整個樹狀目錄中的計算。 當樹狀目錄中的工作取消時，執行階段不會啟動新的工作。 不過，執行階段可讓已開始到完成的工作。 因此，如果是`parallel_for_each`演算法，作用中的迴圈反覆項目可清除其資源。

在此範例中的兩個版本，如果陣列包含多個複本来搜尋之值的多個迴圈反覆項目可以同時設定結果，並取消整體的作業。 如果您的問題需要條件符合時，只有兩項工作會執行工作，您可以使用重要區段，例如同步處理原始物件。

您也可以使用例外狀況處理來取消使用 PPL 的工作。 如需有關取消的詳細資訊，請參閱 < [PPL 中的取消](cancellation-in-the-ppl.md)。

如需詳細資訊`parallel_for_each`和其他平行演算法，請參閱 <<c2> [ 平行演算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`concrt-omp-parallel-any-of.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc /openmp concrt-omp-parallel-any-of.cpp**

## <a name="see-also"></a>另請參閱

[從 OpenMP 移轉至並行執行階段](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[PPL 中的取消](cancellation-in-the-ppl.md)<br/>
[平行演算法](../../parallel/concrt/parallel-algorithms.md)
