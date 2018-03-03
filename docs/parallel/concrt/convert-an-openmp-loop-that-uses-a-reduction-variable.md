---
title: "如何： 轉換使用削減變數來使用並行執行階段的 OpenMP 迴圈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, reduction variables
- reduction variables, converting from OpenMP to the Concurrency Runtime
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f218bbc47fa33e6cc9546d032311417d9e10d554
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-convert-an-openmp-loop-that-uses-a-reduction-variable-to-use-the-concurrency-runtime"></a>如何：轉換使用削減變數的 OpenMP 迴圈來使用並行執行階段
這個範例示範如何將轉換 OpenMP[平行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[如](../../parallel/openmp/reference/for-openmp.md)使用迴圈[減少](../../parallel/openmp/reference/reduction.md)子句來使用並行執行階段。  
  
 OpenMP`reduction`子句可讓您指定一個或多個執行緒私用變數受限於削減作業在平行區域結尾處。 OpenMP 預先定義了一組削減運算子。 每個削減變數必須是純量 (例如， `int`， `long`，和`float`)。 OpenMP 也會定義數個限制削減變數在平行區域中的使用方式。  
  
 平行模式程式庫 (PPL) 提供[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)類別，提供可讓您執行細部運算，然後將這些運算合併成最終的可重複使用、 執行緒區域儲存區結果。 `combinable`類別是純量和複雜類型所做的範本。 若要使用`combinable`類別、 執行子運算的平行建構本文中，然後呼叫[concurrency::combinable::combine](reference/combinable-class.md#combine)或[concurrency::combinable::combine_each](reference/combinable-class.md#combine_each)方法以產生最終的結果。 `combine`和`combine_each`每個方法會採用*結合函式*，指定如何結合的每對元素。 因此，`combinable`類別不會套用至一組固定的削減運算子。  
  
## <a name="example"></a>範例  
 這個範例會使用 OpenMP 與並行執行階段計算前 35 Fibonacci 數字的總和。  
  
 [!code-cpp[concrt-openmp#7](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-a-reduction-variable_1.cpp)]  
  
 此範例會產生下列輸出。  
  
```Output  
Using OpenMP...  
The sum of the first 35 Fibonacci numbers is 14930351.  
Using the Concurrency Runtime...  
The sum of the first 35 Fibonacci numbers is 14930351.  
```  
  
 如需有關`combinable`類別，請參閱[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 範例程式碼複製並將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`concrt-omp-fibonacci-reduction.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe /EHsc /openmp concrt-omp-費式數列-reduction.cpp**  
  
## <a name="see-also"></a>請參閱  
 [從 OpenMP 移轉至並行執行階段](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)

