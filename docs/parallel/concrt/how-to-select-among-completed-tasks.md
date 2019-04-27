---
title: HOW TO：在已完成的工作之中選取
ms.date: 11/04/2016
helpviewer_keywords:
- selecting among completed tasks [Concurrency Runtime]
- completed tasks, selecting among [Concurrency Runtime]
ms.assetid: c8ccc160-043f-4599-847b-32ed270bb257
ms.openlocfilehash: 0d31f9bd16aaa70cc773e60e4f1193e66ec520f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62205638"
---
# <a name="how-to-select-among-completed-tasks"></a>HOW TO：在已完成的工作之中選取

此範例示範如何使用[concurrency:: choice](../../parallel/concrt/reference/choice-class.md)並[concurrency:: join](../../parallel/concrt/reference/join-class.md)類別選取第一個工作完成搜尋演算法。

## <a name="example"></a>範例

下列範例會以平行方式執行兩個搜尋演算法，並選取要完成的第一個演算法。 這個範例會定義`employee`型別，其中包含的數值識別項和薪資的員工。 `find_employee`函式會尋找第一個提供的識別碼或提供的薪資的員工。 `find_employee`函式也會處理任何員工有提供的識別碼或薪資。 `wmain`函式會建立陣列`employee`物件和數個識別項和薪資值的搜尋。

此範例會使用`choice`物件，以選取 在下列案例：

1. 員工的人員提供的識別碼存在。

1. 已提供的薪資的員工存在。

1. 有沒有提供的識別碼或薪資的員工。

針對前兩個案例中，此範例會使用[3&gt;concurrency::single_assignment&lt;3}](../../parallel/concrt/reference/single-assignment-class.md)物件來保存的識別項，而另一個`single_assignment`物件來保存薪資。 此範例會使用`join`第三個案例中的物件。 `join`物件由兩個額外的`single_assignment`物件，一個用於任何具有提供之識別碼的員工的所在，案例，其中一個案例中沒有具有所提供的薪資的員工的所在。 `join`物件傳送訊息，當收到訊息時，每個成員。 在此範例中，`join`物件傳送訊息時不具有提供之識別碼的員工或薪資存在。

此範例會使用[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)物件以平行方式執行這兩個搜尋演算法。 每個搜尋工作寫入其中一個`single_assignment`物件，表示指定的員工是否存在。 此範例會使用[concurrency:: receive](reference/concurrency-namespace-functions.md#receive)函式來取得第一個緩衝區，其中包含訊息的索引和`switch`區塊來列印結果。

[!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/cpp/how-to-select-among-completed-tasks_1.cpp)]

此範例會產生下列輸出。

```Output
Employee with id 14758 has salary 27780.00.
Employee with salary 29150.00 has id 84345.
Employee with id 61935 has salary 29905.00.
No employee has id 899 or salary 31223.00.
```

這個範例會使用[concurrency::make_choice](reference/concurrency-namespace-functions.md#make_choice)協助程式函式來建立`choice`物件並[concurrency::make_join](reference/concurrency-namespace-functions.md#make_join) helper 函式來建立`join`物件。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`find-employee.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc 尋找 employee.cpp**

## <a name="see-also"></a>另請參閱

[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)<br/>
[choice 類別](../../parallel/concrt/reference/choice-class.md)<br/>
[join 類別](../../parallel/concrt/reference/join-class.md)
