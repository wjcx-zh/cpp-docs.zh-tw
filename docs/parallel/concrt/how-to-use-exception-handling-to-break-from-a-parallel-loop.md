---
title: "如何： 使用例外狀況處理來中斷平行迴圈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- search algorithm, writing [Concurrency Runtime]
- writing a search algorithm [Concurrency Runtime]
ms.assetid: 16d7278c-2d10-4014-9f58-f1899e719ff9
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 29140c339614e572733988bd7ca5e14561cee5dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-exception-handling-to-break-from-a-parallel-loop"></a>如何：使用例外狀況處理來中斷平行迴圈
本主題說明如何撰寫基本樹狀結構的搜尋演算法。  
  
 本主題[取消](cancellation-in-the-ppl.md)說明取消在平行模式程式庫中的角色。 使用例外狀況處理會比較沒有效率的方法來取消平行工作比使用[concurrency::task_group::cancel](reference/task-group-class.md#cancel)和[concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel)方法。 但是，情況下，使用例外狀況處理來取消工作是適當的其中一種情況時，您呼叫的協力廠商程式庫會使用工作或平行演算法，但不提供`task_group`或`structured_task_group`取消的物件。  

  
## <a name="example"></a>範例  
 下列範例示範基本`tree`包含資料元素和子節點清單的類型。 下節將說明主體`for_all`方法中，遞迴每個子節點執行的工作函式。  
  
 [!code-cpp[concrt-task-tree-search#2](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_1.cpp)]  
  
## <a name="example"></a>範例  
 下列範例所示`for_all`方法。 它會使用[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)演算法以平行方式樹狀結構的每個節點上執行的工作函式。  
  
 [!code-cpp[concrt-task-tree-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_2.cpp)]  
  
## <a name="example"></a>範例  
 下列範例顯示 `search_for_value` 函式，這個函式會在提供的 `tree` 物件中搜尋值。 此函式會將傳遞至`for_all`發現樹狀節點，其中包含所提供的值時，會擲回的工作函式的方法。  
  
 假設`tree`類別由協力廠商程式庫，和您不能修改它。 使用例外狀況處理適合在此情況下，因為`for_all`方法不會提供`task_group`或`structured_task_group`給呼叫者的物件。 因此，工作函式是無法直接取消其父工作群組。  
  
 當您提供給工作群組的工作函式擲回例外狀況時，執行階段會停止工作群組 （包括任何子工作群組） 中的所有工作，並會捨棄任何尚未開始的工作。 `search_for_value`函式使用`try` - `catch`區塊來擷取例外狀況，並將結果列印至主控台。  
  
 [!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_3.cpp)]  
  
## <a name="example"></a>範例  
 下列範例會建立`tree`物件，並搜尋以平行方式的幾個值。 `build_tree`函式在本主題稍後所示。  
  
 [!code-cpp[concrt-task-tree-search#4](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_4.cpp)]  
  
 這個範例會使用[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)值平行搜尋演算法。 如需有關這個演算法的詳細資訊，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## <a name="example"></a>範例  
 下列完整的範例使用例外狀況處理，來搜尋基本的樹狀結構中的值。  
  
 [!code-cpp[concrt-task-tree-search#5](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_5.cpp)]  
  
 這個範例會產生下列輸出範例。  
  
```Output  
Found a node with value 32614.  
Found a node with value 86131.  
Did not find node with value 17522.  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 範例程式碼複製並將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`task-tree-search.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe /EHsc 工作樹狀結構 search.cpp**  
  
## <a name="see-also"></a>請參閱  
 [PPL 中的取消](cancellation-in-the-ppl.md)   
 [例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [平行演算法](../../parallel/concrt/parallel-algorithms.md)   
 [task_group 類別](reference/task-group-class.md)   
 [structured_task_group 類別](../../parallel/concrt/reference/structured-task-group-class.md)   
 [parallel_for_each 函式](reference/concurrency-namespace-functions.md#parallel_for_each)


