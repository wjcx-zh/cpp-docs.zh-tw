---
title: 如何： 轉換使用例外狀況處理來使用並行執行階段的 OpenMP 迴圈 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exception handling, converting from OpenMP to the Concurrency Runtime
- converting from OpenMP to the Concurrency Runtime, exception handling
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b96273589fb4e7d7e73e7bc72da03a92d5587de8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687799"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-exception-handling-to-use-the-concurrency-runtime"></a>如何：轉換使用例外狀況處理的 OpenMP 迴圈來使用並行執行階段
這個範例示範如何將轉換 OpenMP[平行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[如](../../parallel/openmp/reference/for-openmp.md)執行例外狀況處理來使用並行執行階段例外狀況處理機制的迴圈。  
  
 OpenMP 以及在必須攔截並處理相同的區域中相同的執行緒在平行區域中擲回的例外狀況。 根據預設，終止處理序的未處理例外狀況處理常式會攔截到例外逸出平行區域。  
  

 並行執行階段，當您擲回的例外狀況，例如傳遞給工作群組的工作函式主體中[concurrency:: task_group](reference/task-group-class.md)或[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)物件，或平行演算法，例如[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)，儲存該例外狀況，執行階段，並將其封送處理至等候工作群組或演算法，以完成的內容。 對於工作群組，等候內容是呼叫的內容[task_group](reference/task-group-class.md#wait)， [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait)， [concurrency::task_group::run_and_wait](reference/task-group-class.md#run_and_wait)，或[run_and_wait](reference/structured-task-group-class.md#run_and_wait)。 平行演算法，等候內容會是呼叫該演算法的內容。 執行階段也會停止在工作群組，包括子工作群組中的所有作用中工作，並會捨棄任何尚未開始的工作。  


  
## <a name="example"></a>範例  
 這個範例示範如何處理例外狀況中的 OpenMP`parallel`區域在呼叫`parallel_for`。 `do_work`函式會執行不成功，因此會擲回例外狀況類型的記憶體配置要求[std:: bad_alloc](../../standard-library/bad-alloc-class.md)。 在使用 /openmp 版本中，會擲回例外狀況的執行緒必須也攔截它。 換句話說，OpenMP 平行迴圈的每個反覆項目必須處理的例外狀況。 在使用並行執行階段版本中，主執行緒會攔截另一個執行緒所擲回例外狀況。  
  
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
  
 在這個範例前段使用 OpenMP 版本中，例外狀況中，就會發生，由每個迴圈反覆項目。 中使用並行執行階段版本，執行階段儲存例外狀況、 停止所有作用中工作、 會捨棄任何工作尚未啟動，並封送處理的例外狀況至呼叫的內容`parallel_for`。  
  
 如果您需要使用 OpenMP 版本結束後發生例外狀況，您可以使用布林值旗標來表示其他迴圈反覆項目發生錯誤。 如本主題中範例所示[How to： 轉換的 OpenMP 迴圈來使用並行執行階段，使用取消](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)，如果在設定的旗標，後續的迴圈反覆項目會執行任何動作。 相反地，如果您需要使用並行執行階段迴圈繼續之後發生例外狀況，處理平行迴圈主體本身中的例外狀況。  
  
 並行執行階段非同步代理程式和輕量型工作，例如，其他元件不會傳輸例外狀況。 相反地，根據預設，終止處理序的未處理例外狀況處理常式會攔截到未處理例外狀況。 如需例外狀況處理的詳細資訊，請參閱[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。  
  
 如需有關`parallel_for`和其他平行演算法，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 範例程式碼複製並將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`concrt-omp-exceptions.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe /EHsc /openmp concrt-omp-exceptions.cpp**  
  
## <a name="see-also"></a>另請參閱  
 [從 OpenMP 移轉至並行執行階段](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [平行演算法](../../parallel/concrt/parallel-algorithms.md)

