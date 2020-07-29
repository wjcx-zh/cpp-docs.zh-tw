---
title: 如何：使用例外狀況處理來中斷平行迴圈
ms.date: 11/04/2016
helpviewer_keywords:
- search algorithm, writing [Concurrency Runtime]
- writing a search algorithm [Concurrency Runtime]
ms.assetid: 16d7278c-2d10-4014-9f58-f1899e719ff9
ms.openlocfilehash: 9cf42df0926022f93633a6b5b1365ae9fc646a1a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213914"
---
# <a name="how-to-use-exception-handling-to-break-from-a-parallel-loop"></a>如何：使用例外狀況處理來中斷平行迴圈

本主題說明如何撰寫基本樹狀結構的搜尋演算法。

主題[取消](cancellation-in-the-ppl.md)說明在平行模式程式庫中取消的角色。 使用例外狀況處理比使用[concurrency：： task_group：： cancel](reference/task-group-class.md#cancel)和[concurrency：： structured_task_group：： cancel](reference/structured-task-group-class.md#cancel)方法來取消平行工作是比較有效率的方式。 不過，使用例外狀況處理來取消工作的其中一個案例是，當您呼叫使用工作或平行演算法的協力廠商程式庫，但未提供 `task_group` 要取消的或 `structured_task_group` 物件時。

## <a name="example"></a>範例

下列範例顯示 `tree` 包含資料元素和子節點清單的基本類型。 下節顯示方法的主體 `for_all` ，它會以遞迴方式在每個子節點上執行工作函數。

[!code-cpp[concrt-task-tree-search#2](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_1.cpp)]

## <a name="example"></a>範例

下列範例顯示 `for_all` 方法。 它會使用[concurrency：:p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)演算法，以平行方式在樹狀結構的每個節點上執行工作函數。

[!code-cpp[concrt-task-tree-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_2.cpp)]

## <a name="example"></a>範例

下列範例顯示 `search_for_value` 函式，這個函式會在提供的 `tree` 物件中搜尋值。 此函式會將工作函式傳遞至 `for_all` 方法，當它找到的樹狀節點包含提供的值時，就會擲回此函數。

假設 `tree` 類別是由協力廠商程式庫提供，而且您無法加以修改。 在此情況下，使用例外狀況處理是適當的，因為 `for_all` 方法並不會將 `task_group` 或物件提供 `structured_task_group` 給呼叫者。 因此，工作函式無法直接取消其父工作組。

當您提供給工作組的工作函式擲回例外狀況時，執行時間會停止工作組中的所有工作（包括任何子工作群組），並捨棄尚未啟動的任何工作。 函式會 `search_for_value` 使用 **`try`** - **`catch`** 區塊來捕捉例外狀況，並將結果列印至主控台。

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_3.cpp)]

## <a name="example"></a>範例

下列範例 `tree` 會建立物件，並以平行方式搜尋數個值。 `build_tree`本主題稍後會顯示函數。

[!code-cpp[concrt-task-tree-search#4](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_4.cpp)]

這個範例會使用[concurrency：:p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)演算法，以平行方式搜尋值。 如需這個演算法的詳細資訊，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="example"></a>範例

下列完整範例會使用例外狀況處理來搜尋基本樹狀結構中的值。

[!code-cpp[concrt-task-tree-search#5](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_5.cpp)]

這個範例會產生下列範例輸出。

```Output
Found a node with value 32614.
Found a node with value 86131.
Did not find node with value 17522.
```

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為的檔案中， `task-tree-search.cpp` 然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl.exe/EHsc task-tree-search .cpp**

## <a name="see-also"></a>另請參閱

[PPL 中的取消](cancellation-in-the-ppl.md)<br/>
[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[工作平行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[task_group 類別](reference/task-group-class.md)<br/>
[structured_task_group 類別](../../parallel/concrt/reference/structured-task-group-class.md)<br/>
[parallel_for_each 函式](reference/concurrency-namespace-functions.md#parallel_for_each)
