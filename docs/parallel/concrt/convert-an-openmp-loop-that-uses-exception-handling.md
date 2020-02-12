---
title: 如何：轉換使用例外狀況處理的 OpenMP 迴圈來使用並行執行階段
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling, converting from OpenMP to the Concurrency Runtime
- converting from OpenMP to the Concurrency Runtime, exception handling
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
ms.openlocfilehash: 380a96eedb8a70965197c4a5ce0c5199bc268db5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141807"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-exception-handling-to-use-the-concurrency-runtime"></a>如何：轉換使用例外狀況處理的 OpenMP 迴圈來使用並行執行階段

這個範例示範如何將執行例外狀況處理的 OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../../parallel/openmp/reference/for-openmp.md)迴圈轉換成使用並行執行階段的例外狀況處理機制。

在 OpenMP 中，在平列區域中擲回的例外狀況必須在相同的區域中被攔截並處理，而且同一個執行緒也一樣。 未處理的例外狀況處理常式攔截到平列區域的例外狀況，這會在預設情況下終止進程。

在並行執行階段中，當您在傳遞至工作組的工作函式主體中擲回例外狀況，例如[concurrency：： task_group](reference/task-group-class.md)或[concurrency：： structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)物件，或平行演算法（例如[concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)）時，執行時間會儲存該例外狀況，並將其封送處理至等待工作組或演算法完成的內容。 針對工作組，等待內容是呼叫[concurrency：： task_group：： wait](reference/task-group-class.md#wait)， [concurrency：： structured_task_group：： wait](reference/structured-task-group-class.md#wait)， [concurrency：： task_group：： run_and_wait](reference/task-group-class.md#run_and_wait)，或[concurrency：](reference/structured-task-group-class.md#run_and_wait)： structured_task_group：： run_and_wait 的內容。 針對平行演算法，等待內容是呼叫該演算法的內容。 執行時間也會停止工作組中的所有作用中工作（包括子工作組中的工作），並捨棄尚未啟動的任何工作。

## <a name="example"></a>範例

這個範例示範如何處理 OpenMP `parallel` 區域中的例外狀況，以及呼叫 `parallel_for`。 `do_work` 函式會執行不成功的記憶體配置要求，因此會擲回[std：： bad_alloc](../../standard-library/bad-alloc-class.md)類型的例外狀況。 在使用 OpenMP 的版本中，擲回例外狀況的執行緒也必須加以攔截。 換句話說，OpenMP 平行迴圈的每個反復專案都必須處理例外狀況。 在使用並行執行階段的版本中，主執行緒會攔截由另一個執行緒擲回的例外狀況。

[!code-cpp[concrt-openmp#3](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-exception-handling_1.cpp)]

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

在使用 OpenMP 的這個範例版本中，會在中發生例外狀況，而且會由每個迴圈反復專案處理。 在使用並行執行階段的版本中，執行時間會儲存例外狀況、停止所有作用中的工作、捨棄尚未啟動的任何工作，並將例外狀況封送處理至呼叫 `parallel_for`的內容。

如果您要求使用 OpenMP 的版本在例外狀況發生之後終止，您可以使用布林值旗標來指示發生錯誤的其他迴圈反覆運算。 如[如何：將使用取消的 OpenMP 迴圈轉換成使用並行執行階段](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)主題中的範例所示，如果設定了旗標，後續的迴圈反覆運算將不會執行任何動作。 相反地，如果您要求使用並行執行階段的迴圈會在例外狀況發生之後繼續，請在平行迴圈主體本身中處理例外狀況。

並行執行階段的其他元件（例如非同步代理程式和輕量工作）不會傳輸例外狀況。 相反地，未處理的例外狀況處理常式會攔截未處理的例外狀況，這會在預設情況下終止進程。 如需例外狀況處理的詳細資訊，請參閱[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。

如需 `parallel_for` 和其他平行演算法的詳細資訊，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為 `concrt-omp-exceptions.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl/EHsc/openmp concrt-omp-exceptions .cpp**

## <a name="see-also"></a>另請參閱

[從 OpenMP 移轉至並行執行階段](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[平行演算法](../../parallel/concrt/parallel-algorithms.md)
