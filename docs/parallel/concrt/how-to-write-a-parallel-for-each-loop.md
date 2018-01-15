---
title: "如何： 撰寫 parallel_for_each 迴圈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- writing a parallel_for_each loop [Concurrency Runtime]
- parallel_for_each function, example
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 179fa4b055b4743303f5d72ebec851a1d10def93
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-write-a-parallelforeach-loop"></a>如何：撰寫 parallel_for_each 迴圈
這個範例示範如何使用[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)演算法來計算中質數的計數[std:: array](../../standard-library/array-class-stl.md)平行的物件。  
  
## <a name="example"></a>範例  
 下列範例計算陣列中質數的計數兩次。 此範例會先使用[std:: for_each](../../standard-library/algorithm-functions.md#for_each)循序計算計數的演算法。 然後此範例使用`parallel_for_each`演算法以平行方式執行相同的工作。 這個範例也會將執行這兩項計算所需的時間列印到主控台。  
  
 [!code-cpp[concrt-parallel-count-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-each-loop_1.cpp)]  
  
 下列範例輸出適用於具有四個處理器的電腦。  
  
```Output  
serial version:  
found 17984 prime numbers  
took 6115 ms  
 
parallel version:  
found 17984 prime numbers  
took 1653 ms  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯程式碼，將它複製然後將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`parallel-count-primes.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe /EHsc 平行計數 primes.cpp**  
  
## <a name="robust-programming"></a>穩固程式設計  
 此範例將傳遞至 lambda 運算式`parallel_for_each`演算法會使用`InterlockedIncrement`函式可啟用同時遞增計數器迴圈的平行反覆項目。 如果您使用函式，例如`InterlockedIncrement`來同步處理對共用資源的存取，您可以在程式碼中呈現效能瓶頸。 您可以使用無鎖定的同步處理機制，例如， [concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)類別，以消除同時存取共用資源。 如需範例，會使用`combinable`類別以這種方式，請參閱[How to： 使用可組合的類別改善效能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)。  
  
## <a name="see-also"></a>請參閱  
 [平行演算法](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_for_each 函式](reference/concurrency-namespace-functions.md#parallel_for_each)


