---
title: 如何：使用 parallel_invoke 執行平行作業
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_invoke function, example
- calling multiple functions in parallel [Concurrency Runtime]
ms.assetid: a6aea69b-d647-4b7e-bf3b-e6a6a9880072
ms.openlocfilehash: 2d4cd19a3cbb02b9c18b1733f8df6f64eb956803
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473680"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>如何：使用 parallel_invoke 執行平行作業

此範例示範如何使用[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)演算法，以改善程式執行共用的資料來源上的多個作業的效能。 沒有作業修改的來源，因為它們可以平行執行簡單的方式。

## <a name="example"></a>範例

請考慮下列程式碼範例會建立型別的變數`MyDataType`、 呼叫來初始化該變數中，函式，然後執行 多長時間的作業，對該資料。

[!code-cpp[concrt-parallel-word-mining#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_1.cpp)]

如果`lengthy_operation1`， `lengthy_operation2`，並`lengthy_operation3`函式不會修改`MyDataType`變數，這些函式可以平行執行而不需要進行其他修改。

## <a name="example"></a>範例

下列範例會修改前一個範例，以平行方式執行。 `parallel_invoke`演算法以平行方式執行每項工作並在所有工作都完成時返回。

[!code-cpp[concrt-parallel-word-mining#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_2.cpp)]

## <a name="example"></a>範例

下列範例會下載*The Iliad*藉由從 gutenberg.org Homer 和執行多項作業對該檔案。 此範例會先以序列方式執行這些作業，並再以平行方式執行相同的作業。

[!code-cpp[concrt-parallel-word-mining#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_3.cpp)]

此範例會產生下列輸出範例。

```Output
Downloading 'The Iliad'...

Running serial version... took 953 ms.
Running parallel version... took 656 ms.

The most common words that have five or more letters are:
    their (953)
    shall (444)
    which (431)
    great (398)
    Hector (349)
    Achilles (309)
    through (301)
    these (268)
    chief (259)
The longest sequence of words that have the same first letter is:
    through the tempest to the tented
The following palindromes appear in the text:
    spots stops
    speed deeps
    keels sleek
```

這個範例會使用`parallel_invoke`演算法來呼叫多個函式相同的資料來源上的該動作。 您可以使用`parallel_invoke`演算法以平行方式，不只處理相同的資料呼叫任何一組的函式。

因為`parallel_invoke`演算法以平行方式呼叫每個工作函式，其效能會受限於耗用最長的時間才能完成 （亦即，如果執行階段會處理不同的處理器上的每個函式） 的函式。 此範例會執行更多的工作，以平行方式比可用處理器數目，如果多個工作可以執行每個處理器上。 在此情況下，效能會受限於所耗用最長的時間才能完成之工作的群組。

此範例會以平行方式執行三項工作，因為您不應預期有三個以上處理器的電腦上調整規模的效能。 若要改善效能的更多，您可以最長執行的工作分成較小的工作，並以平行方式執行這些工作。

您可以使用`parallel_invoke`演算法，而非[concurrency:: task_group](reference/task-group-class.md)並[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)類別，如果您不需要支援取消。 如需比較的使用方式的範例`parallel_invoke`演算法，與工作群組，請參閱[如何： 使用 parallel_invoke 撰寫平行排序常式](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)。

## <a name="compiling-the-code"></a>編譯程式碼

若要編譯程式碼，將它複製然後將它貼在 Visual Studio 專案中，或將它貼在檔案，稱為`parallel-word-mining.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc /MD/DUNICODE /D_AFXDLL 平行 word mining.cpp**

## <a name="see-also"></a>另請參閱

[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_invoke 函式](reference/concurrency-namespace-functions.md#parallel_invoke)

