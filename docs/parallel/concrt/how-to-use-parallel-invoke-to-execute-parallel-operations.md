---
title: 如何：使用 parallel_invoke 執行平行作業
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_invoke function, example
- calling multiple functions in parallel [Concurrency Runtime]
ms.assetid: a6aea69b-d647-4b7e-bf3b-e6a6a9880072
ms.openlocfilehash: 199b663331e3322601100206f222e80bbb7c8db0
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142261"
---
# <a name="how-to-use-parallel_invoke-to-execute-parallel-operations"></a>如何：使用 parallel_invoke 執行平行作業

這個範例示範如何使用[concurrency：:p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)演算法來改善在共用資料來源上執行多個作業的程式效能。 因為沒有任何作業會修改來源，所以可以直接以平行方式執行。

## <a name="example"></a>範例

請考慮下列會建立類型變數 `MyDataType`的程式碼範例，會呼叫函式來初始化該變數，然後在該資料上執行多個冗長的作業。

[!code-cpp[concrt-parallel-word-mining#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_1.cpp)]

如果 `lengthy_operation1`、`lengthy_operation2`和 `lengthy_operation3` 函數不會修改 `MyDataType` 變數，則這些函式可以平行執行，而不需要進行其他修改。

## <a name="example"></a>範例

下列範例會修改上一個範例，以平行方式執行。 `parallel_invoke` 演算法會平行執行每個工作，並在所有工作完成後傳回。

[!code-cpp[concrt-parallel-word-mining#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_2.cpp)]

## <a name="example"></a>範例

下列範例會從 gutenberg.org 下載*Iliad* by Homer，並在該檔案上執行多項作業。 此範例會先以序列方式執行這些作業，然後平行執行相同的作業。

[!code-cpp[concrt-parallel-word-mining#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_3.cpp)]

這個範例會產生下列範例輸出。

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

這個範例會使用 `parallel_invoke` 演算法來呼叫在相同資料來源上作用的多個函數。 您可以使用 `parallel_invoke` 演算法，以平行方式呼叫任何一組函式，而不只是作用於相同資料的函數。

由於 `parallel_invoke` 演算法會以平行方式呼叫每個工作函式，因此其效能會受到花費最長時間完成的函式所限制（也就是，如果執行時間處理個別處理器上的每個函數）。 如果此範例執行的工作數目與可用處理器的數量平行，則可以在每個處理器上執行多個工作。 在此情況下，效能會受限於花費最長時間完成的一組工作。

由於此範例會平行執行三個工作，因此您應該不會預期在具有三個以上處理器的電腦上調整效能。 若要改善效能，您可以將執行時間最長的工作分成較小的工作，並平行執行這些工作。

如果您不需要取消支援，您可以使用 `parallel_invoke` 演算法，而不是[concurrency：： task_group](reference/task-group-class.md)和[concurrency：： structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)類別。 如需比較 `parallel_invoke` 演算法與工作組用法的範例，請參閱[如何：使用 Parallel_invoke 撰寫平行排序常式](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)。

## <a name="compiling-the-code"></a>編譯程式碼

若要編譯器代碼，請複製該程式碼，然後將它貼入 Visual Studio 專案中，或貼入名為 `parallel-word-mining.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl/EHsc/MD/DUNICODE/D_AFXDLL parallel-word-mining.cpp .cpp**

## <a name="see-also"></a>另請參閱

[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_invoke 函式](reference/concurrency-namespace-functions.md#parallel_invoke)
