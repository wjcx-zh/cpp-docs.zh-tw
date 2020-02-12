---
title: 如何：在已完成的工作之中選取
ms.date: 11/04/2016
helpviewer_keywords:
- selecting among completed tasks [Concurrency Runtime]
- completed tasks, selecting among [Concurrency Runtime]
ms.assetid: c8ccc160-043f-4599-847b-32ed270bb257
ms.openlocfilehash: 75ecac8dd0e8845401e3e287e8c95ea614055970
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142477"
---
# <a name="how-to-select-among-completed-tasks"></a>如何：在已完成的工作之中選取

這個範例示範如何使用[concurrency：： choice](../../parallel/concrt/reference/choice-class.md)和[concurrency：： join](../../parallel/concrt/reference/join-class.md)類別來選取要完成搜尋演算法的第一個工作。

## <a name="example"></a>範例

下列範例會平行執行兩個搜尋演算法，並選取要完成的第一個演算法。 這個範例會定義 `employee` 類型，其中保存員工的數值識別碼和薪資。 `find_employee` 函式會尋找具有所提供識別碼或所提供薪資的第一個員工。 `find_employee` 函數也會處理沒有任何員工提供的識別碼或薪資的情況。 `wmain` 函式會建立 `employee` 物件的陣列，並搜尋數個識別碼和薪資值。

此範例會使用 `choice` 物件，在下列情況中進行選取：

1. 有提供識別碼的員工存在。

1. 有提供薪資的員工存在。

1. 沒有提供識別碼或薪資的員工存在。

在前兩個案例中，此範例會使用[concurrency：： single_assignment](../../parallel/concrt/reference/single-assignment-class.md)物件來保存識別碼，而將另一個 `single_assignment` 物件用於保存薪資。 此範例會使用第三個案例的 `join` 物件。 `join` 物件是由兩個額外的 `single_assignment` 物件所組成，一個用於沒有提供之識別碼的員工存在，另一個則適用于沒有提供薪資的員工存在的情況。 `join` 物件會在其每個成員收到訊息時傳送訊息。 在此範例中，當沒有提供識別碼或薪資的員工存在時，`join` 物件就會傳送訊息。

此範例會使用[concurrency：： structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)物件，以平行方式執行這兩個搜尋演算法。 每個搜尋工作都會寫入其中一個 `single_assignment` 物件，以指出給定的員工是否存在。 此範例使用[concurrency：： receive](reference/concurrency-namespace-functions.md#receive)函數取得包含訊息的第一個緩衝區索引，以及用來列印結果的 `switch` 區塊。

[!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/cpp/how-to-select-among-completed-tasks_1.cpp)]

此範例會產生下列輸出。

```Output
Employee with id 14758 has salary 27780.00.
Employee with salary 29150.00 has id 84345.
Employee with id 61935 has salary 29905.00.
No employee has id 899 or salary 31223.00.
```

這個範例會使用[concurrency：： make_choice](reference/concurrency-namespace-functions.md#make_choice) helper 函式來建立 `choice` 物件，並使用[concurrency：： make_join](reference/concurrency-namespace-functions.md#make_join) helper 函式來建立 `join` 物件。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為 `find-employee.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl/EHsc find-employee .cpp**

## <a name="see-also"></a>另請參閱

[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)<br/>
[choice 類別](../../parallel/concrt/reference/choice-class.md)<br/>
[join 類別](../../parallel/concrt/reference/join-class.md)
