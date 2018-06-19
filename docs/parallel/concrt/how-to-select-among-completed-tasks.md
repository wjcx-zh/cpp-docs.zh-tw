---
title: 如何： 在已完成的工作之中選取 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- selecting among completed tasks [Concurrency Runtime]
- completed tasks, selecting among [Concurrency Runtime]
ms.assetid: c8ccc160-043f-4599-847b-32ed270bb257
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a485eb87f2caa62a382983c1cda2b9c098742d42
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687110"
---
# <a name="how-to-select-among-completed-tasks"></a>如何：在已完成的工作之中選取
這個範例示範如何使用[concurrency:: choice](../../parallel/concrt/reference/choice-class.md)和[concurrency:: join](../../parallel/concrt/reference/join-class.md)類別選取第一個工作完成搜尋演算法。  
  
## <a name="example"></a>範例  
 下列範例會以平行方式執行兩種搜尋演算法，並選取要完成的第一個演算法。 這個範例會定義`employee`包含員工的數值識別項和薪資的類型。 `find_employee`函式會尋找第一個提供的識別項或提供的薪資的員工。 `find_employee`函式也會處理任何員工有提供的識別項或薪資。 `wmain`函式建立的陣列`employee`物件並搜尋識別項和薪資的數個值。  
  
 此範例會使用`choice`在下列情況下選取的物件：  
  
1.  已提供的識別項的員工存在。  
  
2.  存在有提供的薪資的員工。  
  
3.  沒有具有所提供的識別項或薪資的員工存在。  
  
 前兩個情況下，此範例會使用[concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md)物件來保存識別項，而另一個`single_assignment`物件來保存薪資。 此範例會使用`join`第三個案例的物件。 `join`物件由兩個額外`single_assignment`物件提供的識別項的任何員工有存在，在案例，一個沒有具有所提供的薪資的員工所在的情況。 `join`物件傳送訊息，當接收訊息時，每個成員。 在此範例中，`join`物件傳送訊息時沒有具有所提供的識別項的員工或薪資存在。  
  
 此範例會使用[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)以平行方式執行這兩個搜尋演算法的物件。 每個搜尋工作寫入其中的`single_assignment`指出給定的員工是否存在的物件。 此範例會使用[concurrency:: receive](reference/concurrency-namespace-functions.md#receive)函式可取得包含訊息的第一個緩衝區的索引和`switch`區塊，以將結果列印。  
  
 [!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/cpp/how-to-select-among-completed-tasks_1.cpp)]  
  
 此範例會產生下列輸出。  
  
```Output  
Employee with id 14758 has salary 27780.00.  
Employee with salary 29150.00 has id 84345.  
Employee with id 61935 has salary 29905.00.  
No employee has id 899 or salary 31223.00.  
```  
  
 這個範例會使用[concurrency::make_choice](reference/concurrency-namespace-functions.md#make_choice) helper 函式來建立`choice`物件和[concurrency::make_join](reference/concurrency-namespace-functions.md#make_join) helper 函式來建立`join`物件。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 範例程式碼複製並將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`find-employee.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe /EHsc 尋找 employee.cpp**  
  
## <a name="see-also"></a>另請參閱  
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)   
 [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)   
 [choice 類別](../../parallel/concrt/reference/choice-class.md)   
 [join 類別](../../parallel/concrt/reference/join-class.md)
