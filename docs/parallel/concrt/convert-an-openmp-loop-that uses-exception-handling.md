---
title: 如何：轉換使用例外狀況處理的 OpenMP 迴圈來使用並行執行階段
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling, converting from OpenMP to the Concurrency Runtime
- converting from OpenMP to the Concurrency Runtime, exception handling
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
ms.openlocfilehash: f47beb7deffa0511e707768d2a1a84f47e489d5e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608399"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-exception-handling-to-use-the-concurrency-runtime"></a>如何：轉換使用例外狀況處理的 OpenMP 迴圈來使用並行執行階段

此範例示範如何將轉換 OpenMP[平行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[如](../../parallel/openmp/reference/for-openmp.md)執行例外狀況處理，以使用並行執行階段例外狀況處理機制的迴圈。

在 OpenMP 平行區域中會擲回的例外狀況必須攔截並處理相同的區域中的同一個執行緒。 根據預設，終止處理序的未處理的例外狀況處理常式會攔截到例外逸出平行區域。

並行執行階段，當您擲回的例外狀況，例如將工作群組的工作函式主體中時[concurrency:: task_group](reference/task-group-class.md)或是[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)物件，或這類的平行演算法[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)，執行階段會儲存該例外狀況，並將它封送處理至等候工作群組或演算法來完成的內容。 針對工作群組，等候內容為呼叫的內容[2&gt;concurrency::task_group::wait&lt;2](reference/task-group-class.md#wait)， [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait)， [concurrency::task_group::run_and_wait](reference/task-group-class.md#run_and_wait)，或[run_and_wait](reference/structured-task-group-class.md#run_and_wait)。 平行演算法，等候內容會為呼叫該演算法的內容。 執行階段也會停止在工作群組中，包括子工作群組中的所有作用中工作，並會捨棄任何尚未開始的工作。

## <a name="example"></a>範例

此範例示範如何處理例外狀況中的 OpenMP`parallel`區域並在呼叫`parallel_for`。 `do_work`函式會執行的記憶體配置要求不成功，因此會擲回例外狀況型別的[std:: bad_alloc](../../standard-library/bad-alloc-class.md)。 在使用 OpenMP 的版本，則會擲回例外狀況的執行緒必須也攔截它。 換句話說，OpenMP 平行迴圈的每個反覆項目必須處理的例外狀況。 在使用並行執行階段版本中，主執行緒會攔截另一個執行緒所擲回例外狀況。

[!code-cpp[concrt-openmp#3](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that uses-exception-handling_1.cpp)]

此範例會產生下列輸出。

```Output
Using OpenMP...
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
Using the Concurrency Runtime...
An error of type 'class std::bad_alloc' occurred.
```

在此範例是使用 OpenMP 版本中，例外狀況會發生，且由每個迴圈反覆項目。 在使用並行執行階段版本中，執行階段儲存例外狀況、 停止所有作用中工作，會捨棄任何尚未啟動的工作和封送處理的例外狀況至呼叫的內容`parallel_for`。

如果您需要使用 OpenMP 的版本終止會發生例外狀況之後，您可以使用布林值旗標來通知其他迴圈反覆項目發生錯誤。 主題中範例所示[如何： 轉換的 OpenMP 迴圈來使用並行執行階段，會使用取消](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)，如果設定此旗標，後續的迴圈反覆項目會執行任何動作。 相反地，如果您需要使用並行執行階段迴圈會繼續之後發生的例外狀況，處理平行迴圈主體本身中的例外狀況。

並行執行階段，例如非同步代理程式和輕量型工作，其他元件不會傳輸例外狀況。 相反地，根據預設，終止處理序的未處理的例外狀況處理常式會攔截到未處理例外狀況。 如需例外狀況處理的詳細資訊，請參閱[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。

如需詳細資訊`parallel_for`和其他平行演算法，請參閱 <<c2> [ 平行演算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`concrt-omp-exceptions.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc /openmp concrt-omp-exceptions.cpp**

## <a name="see-also"></a>另請參閱

[從 OpenMP 移轉至並行執行階段](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[平行演算法](../../parallel/concrt/parallel-algorithms.md)

