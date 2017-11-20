---
title: "如何： 轉換使用並行執行階段使用取消的 OpenMP 迴圈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, cancellation
- cancellation, converting from OpenMP to the Concurrency Runtime
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f70ef6431f8dab37b6df185efe1c7494ff0d9b1f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-convert-an-openmp-loop-that-uses-cancellation-to-use-the-concurrency-runtime"></a>如何：轉換使用取消的 OpenMP 迴圈來使用並行執行階段
某些平行迴圈不需要執行所有的反覆項目。 例如，搜尋值的演算法可以終止之後在找到的值。 OpenMP 不提供一個機制來中斷平行迴圈。 不過，您可以使用布林值或旗標，以便表示方案已找到迴圈的反覆項目。 並行執行階段提供功能，可讓一項工作來取消尚未開始的其他工作。  
  
 這個範例示範如何將轉換 OpenMP[平行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[如](../../parallel/openmp/reference/for-openmp.md)迴圈來使用並行執行階段取消機制，不需要執行的所有反覆項目。  
  
## <a name="example"></a>範例  

 這個範例會使用 OpenMP 與並行執行階段實作的平行版本[std::any_of](../../standard-library/algorithm-functions.md#any_of)演算法。 此範例中的 OpenMP 版本會使用旗標來協調之間所有平行迴圈反覆項目尚未符合條件。 使用 並行執行階段的版本會使用[concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel)符合條件時，停止整體作業的方法。  

  
 [!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]  
  
 此範例會產生下列輸出。  
  
```Output  
Using OpenMP...  
9114046 is in the array.  
Using the Concurrency Runtime...  
9114046 is in the array.  
```  
  
 在使用 /openmp 版本中，所有反覆項目迴圈的執行，即使當旗標設定。 此外，如果工作有任何子工作，此旗標也必須可用來傳達取消這些子工作。 並行執行階段中時取消工作群組，則執行階段會取消工作，包含子工作的整個樹狀目錄。 [Concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)演算法使用工作來執行工作。 因此時一次的迴圈反覆運算取消根工作，, 也會取消整個樹狀結構的計算。 當取消工作的樹狀結構，則執行階段不會啟動新的工作。 不過，執行階段會允許已開始到完成的工作。 因此，如果是`parallel_for_each`演算法、 使用中的迴圈反覆項目可以清除其資源。  
  
 在這兩個版本的此範例中，如果陣列包含多個複本来搜尋之值的多個迴圈反覆項目可以每個同時將結果，並取消整體作業。 如果您的問題需要符合條件時，只有一個工作會執行工作，您可以使用例如關鍵區段中，同步處理原始物件。  
  
 您也可以使用例外狀況處理來取消使用 PPL 的工作。 如需取消的詳細資訊，請參閱[PPL 中的取消](cancellation-in-the-ppl.md)。  
  
 如需有關`parallel_for_each`和其他平行演算法，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 範例程式碼複製並將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`concrt-omp-parallel-any-of.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe /EHsc /openmp concrt-omp-平行-any-of.cpp**  
  
## <a name="see-also"></a>另請參閱  
 [從 OpenMP 移轉至並行執行階段](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [PPL 中的取消](cancellation-in-the-ppl.md)   
 [平行演算法](../../parallel/concrt/parallel-algorithms.md)

